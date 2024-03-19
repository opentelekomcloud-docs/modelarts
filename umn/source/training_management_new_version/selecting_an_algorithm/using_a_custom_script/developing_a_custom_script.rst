:original_name: modelarts_23_0240_0.html

.. _modelarts_23_0240_0:

Developing a Custom Script
==========================

Before you use a custom script to create an algorithm, develop the algorithm code. This section describes how to modify local code for model training on ModelArts.

When creating an algorithm, set the code directory, boot file, input path, and output path. These settings enable the interaction between your codes and ModelArts.

-  Code directory

   Specify the code directory in the OBS bucket and upload training data such as training code, dependency installation packages, or pre-generated model to the directory. After you create the training job, ModelArts downloads the code directory and its subdirectories to the container.

   Do not store training data in the code directory. When the training job starts, the data stored in the code directory will be downloaded to the backend. A large amount of training data may lead to a download failure. It is recommended that the size of the code directory does not exceed 50 MB.

-  Boot file

   The boot file in the code directory is used to start the training. Only Python boot files are supported.

-  .. _modelarts_23_0240_0__en-us_topic_0000001133191548_en-us_topic_0000001072715070_li1463111565413:

   Input path

   The training data must be uploaded to an OBS bucket or stored in the dataset. In the training code, :ref:`the input path <modelarts_23_0240_0__en-us_topic_0000001133191548_en-us_topic_0000001072715070_li1463111565413>` must be parsed. ModelArts automatically downloads the data in the input path to the local container directory for training. Ensure that you have the read permission to the OBS bucket. After the training job is started, ModelArts mounts a disk to the **/cache** directory. You can use this directory to store temporary files. For details about the size of the **/cache** directory, see :ref:`What Are Sizes of the /cache Directories for Different Resource Specifications in the Training Environment? <modelarts_05_0090>`

-  Output path

   You are advised to set an empty directory as the training output path. In the training code, :ref:`the output path <modelarts_23_0240_0__en-us_topic_0000001133191548_en-us_topic_0000001072715070_section16262114175610>` must be parsed. ModelArts automatically uploads the training output to the output path. Ensure that you have the write and read permissions to the OBS bucket.

The following section describes how to develop training code in ModelArts.

(Optional) Introducing Dependencies
-----------------------------------

#. If your model references other dependencies, place the required file or installation package in **Code Directory** you set during algorithm creation.

   -  For details about how to install the Python dependency package, see :ref:`How Do I Create a Training Job When a Dependency Package Is Referenced by the Model to Be Trained? <modelarts_05_0063>`
   -  For details about how to install a C++ dependency library, see :ref:`How Do I Install a Library That C++ Depends on? <modelarts_05_0088>`
   -  For details about how to load parameters to a pre-trained model, see :ref:`How Do I Load Some Well Trained Parameters During Job Training? <modelarts_05_0091>` in FAQs.

.. _modelarts_23_0240_0__en-us_topic_0000001133191548_en-us_topic_0000001072715070_section16262114175610:

Parsing Input and Output Paths
------------------------------

When a ModelArts model reads data stored in OBS or outputs data to a specified OBS path, perform the following operations to configure the input and output data:

#. Parse the input and output paths in the training code. The following method is recommended:

   ::

      import argparse
      # Create a parsing task.
      parser = argparse.ArgumentParser(description="train mnist",
                                       formatter_class=argparse.ArgumentDefaultsHelpFormatter)
      # Add parameters.
      parser.add_argument('--train_url', type=str,
                          help='the path model saved')
      parser.add_argument('--data_url', type=str, help='the training data')
      # Parse the parameters.
      args, unkown = parser.parse_known_args()

   After the parameters are parsed, use **data_url** and **train_url** to replace the paths to the data source and the data output, respectively.

#. When using a custom script to create an algorithm, configure the input and output parameters on the **Create Algorithm** page based on code settings.

   -  Training data is a must for algorithm development. By default, the input data is **Data Source** and the code path parameter is **data_url** (customizable).


      .. figure:: /_static/images/en-us_image_0000001852057389.png
         :alt: **Figure 1** Parsing the input path parameter **data_url**

         **Figure 1** Parsing the input path parameter **data_url**

   -  After model training is complete, the trained model and the output information must be stored in an OBS path. By default, the output data is **Output Data** and the code path parameter is **train_url** (customizable).


      .. figure:: /_static/images/en-us_image_0000001852057785.png
         :alt: **Figure 2** Parsing the output path parameter **train_url**

         **Figure 2** Parsing the output path parameter **train_url**

#. When creating a training job, set the input and output paths.

   Select the OBS path or dataset path as the training input, and the OBS path as the output.


   .. figure:: /_static/images/en-us_image_0000001805379758.png
      :alt: **Figure 3** Setting training input and output

      **Figure 3** Setting training input and output

Compiling Training Code and Saving the Model
--------------------------------------------

Training code and the code for saving the model are closely related to the AI engine you use. The following uses the TensorFlow framework as an example. In the training code, the TensorFlow API **tf.flags.FLAGS** is used to receive CLI parameters.

.. code-block::

   from __future__ import absolute_import
   from __future__ import division
   from __future__ import print_function

   import os

   import tensorflow as tf
   from tensorflow.examples.tutorials.mnist import input_data

   import moxing as mox

   tf.flags.DEFINE_integer('max_steps', 1000, 'number of training iterations.')
   tf.flags.DEFINE_string('data_url', '/home/jnn/nfs/mnist', 'dataset directory.')
   tf.flags.DEFINE_string('train_url', '/home/jnn/temp/delete', 'saved model directory.')

   FLAGS = tf.flags.FLAGS


   def main(*args):
       # Train model
       print('Training model...')
       mnist = input_data.read_data_sets(FLAGS.data_url, one_hot=True)
       sess = tf.InteractiveSession()
       serialized_tf_example = tf.placeholder(tf.string, name='tf_example')
       feature_configs = {'x': tf.FixedLenFeature(shape=[784], dtype=tf.float32),}
       tf_example = tf.parse_example(serialized_tf_example, feature_configs)
       x = tf.identity(tf_example['x'], name='x')
       y_ = tf.placeholder('float', shape=[None, 10])
       w = tf.Variable(tf.zeros([784, 10]))
       b = tf.Variable(tf.zeros([10]))
       sess.run(tf.global_variables_initializer())
       y = tf.nn.softmax(tf.matmul(x, w) + b, name='y')
       cross_entropy = -tf.reduce_sum(y_ * tf.log(y))

       tf.summary.scalar('cross_entropy', cross_entropy)

       train_step = tf.train.GradientDescentOptimizer(0.01).minimize(cross_entropy)

       correct_prediction = tf.equal(tf.argmax(y, 1), tf.argmax(y_, 1))
       accuracy = tf.reduce_mean(tf.cast(correct_prediction, 'float'))
       tf.summary.scalar('accuracy', accuracy)
       merged = tf.summary.merge_all()
       test_writer = tf.summary.FileWriter(FLAGS.train_url, flush_secs=1)

       for step in range(FLAGS.max_steps):
           batch = mnist.train.next_batch(50)
           train_step.run(feed_dict={x: batch[0], y_: batch[1]})
           if step % 10 == 0:
               summary, acc = sess.run([merged, accuracy], feed_dict={x: mnist.test.images, y_: mnist.test.labels})
               test_writer.add_summary(summary, step)
               print('training accuracy is:', acc)
       print('Done training!')

       builder = tf.saved_model.builder.SavedModelBuilder(os.path.join(FLAGS.train_url, 'model'))

       tensor_info_x = tf.saved_model.utils.build_tensor_info(x)
       tensor_info_y = tf.saved_model.utils.build_tensor_info(y)

       prediction_signature = (
           tf.saved_model.signature_def_utils.build_signature_def(
               inputs={'images': tensor_info_x},
               outputs={'scores': tensor_info_y},
               method_name=tf.saved_model.signature_constants.PREDICT_METHOD_NAME))

       builder.add_meta_graph_and_variables(
           sess, [tf.saved_model.tag_constants.SERVING],
           signature_def_map={
               'predict_images':
                   prediction_signature,
           },
           main_op=tf.tables_initializer(),
           strip_default_attrs=True)

       builder.save()

       print('Done exporting!')


   if __name__ == '__main__':
       tf.app.run(main=main)

Differences in Training Code Adaptation
---------------------------------------

In the old version, you are required to configure data input and output as follows:

.. code-block::

   # Parse CLI parameters.
   import argparse
   parser = argparse.ArgumentParser(description='MindSpore Lenet Example')
   parser.add_argument('--data_url', type=str, default="./Data",
                       help='path where the dataset is saved')
   parser.add_argument('--train_url', type=str, default="./Model", help='if is test, must provide\
                       path where the trained ckpt file')
   args = parser.parse_args()
   ...
   # Download data to your local container. In the code, local_data_path specifies the training input path.
   mox.file.copy_parallel(args.data_url, local_data_path)
   ...
   # Upload the local container data to the OBS path.
   mox.file.copy_parallel(local_output_path, args.train_url)
