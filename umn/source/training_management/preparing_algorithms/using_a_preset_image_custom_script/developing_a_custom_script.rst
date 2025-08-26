:original_name: develop-modelarts-0008.html

.. _develop-modelarts-0008:

Developing a Custom Script
==========================

Before you use a preset image to create an algorithm, develop the algorithm code. This section describes how to modify local code for model training on ModelArts.

When creating an algorithm, set the code directory, boot file, input path, and output path. These settings enable the interaction between your code and ModelArts.

-  Code directory

   Specify the code directory in the OBS bucket and upload training data such as training code, dependency installation packages, or pre-generated model to the directory. After you create a training job, ModelArts downloads the code directory and its subdirectories to the container.

   Take OBS path **obs://obs-bucket/training-test/demo-code** as an example. The content in the OBS path will be automatically downloaded to **${MA_JOB_DIR}/demo-code** in the training container, and **demo-code** (customizable) is the last-level directory of the OBS path.

   Do not store training data in the code directory. When the training job starts, the data stored in the code directory will be downloaded to the backend. A large amount of training data may lead to a download failure. It is recommended that the size of the code directory does not exceed 50 MB.

-  Boot file

   The boot file in the code directory is used to start the training. Only Python boot files are supported.

-  .. _en-us_topic_0000002340887412__en-us_topic_0000001133191548_en-us_topic_0000001072715070_li1463111565413:

   Input path

   The training data must be uploaded to an OBS bucket or stored in the dataset. In the training code, :ref:`the input path <en-us_topic_0000002340887412__en-us_topic_0000001133191548_en-us_topic_0000001072715070_li1463111565413>` must be parsed. ModelArts automatically downloads the data in the input path to the local container directory for training. Ensure that you have the read permission on the OBS bucket. After the training job is started, ModelArts mounts a disk to the **/cache** directory. You can use this directory to store temporary files. For details about the size of the **/cache** directory, see "What Are Sizes of the /cache Directories for Different Resource Specifications in the Training Environment?" in *FAQ*

-  Output path

   You are advised to set an empty directory as the training output path. In the training code, :ref:`the output path <en-us_topic_0000002340887412__en-us_topic_0000001133191548_en-us_topic_0000001072715070_section16262114175610>` must be parsed. ModelArts automatically uploads the training output to the output path. Ensure that you have the write and read permissions on the OBS bucket.

The following section describes how to develop training code in ModelArts.

(Optional) Introducing Dependencies
-----------------------------------

#. If your model references other dependencies, place the required file or installation package in **Code Directory** you set during algorithm creation.

   -  For details about how to install the Python dependency package, see "How Do I Create a Training Job When a Dependency Package Is Referenced by the Model to Be Trained?" in *FAQs*.
   -  For details about how to install a C++ dependency library, see "How Do I Install a Library That C++ Depends on?" in *FAQs*.
   -  For details about how to load parameters to a pre-trained model, see "How Do I Load Some Well Trained Parameters During Job Training?" in *FAQs*.

.. _en-us_topic_0000002340887412__en-us_topic_0000001133191548_en-us_topic_0000001072715070_section16262114175610:

Parsing Input and Output Paths
------------------------------

To enable a ModelArts model reads data stored in OBS or outputs data to a specified OBS path, follow these steps to configure the input and output data:

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

#. When using a custom script to create an algorithm, configure the input and output parameters on the algorithm creation page based on code settings.

   -  Training data is a must for algorithm development. By default, the input data is **Data Source** and the code path parameter is **data_url** (customizable).


      .. figure:: /_static/images/en-us_image_0000002340728084.png
         :alt: **Figure 1** Parsing the input path parameter **data_url**

         **Figure 1** Parsing the input path parameter **data_url**

   -  After model training is complete, the trained model and the output data must be stored in an OBS path. By default, the output data is **Output Data** and the code path parameter is **train_url** (customizable).


      .. figure:: /_static/images/en-us_image_0000002340887788.png
         :alt: **Figure 2** Parsing the output path parameter **train_url**

         **Figure 2** Parsing the output path parameter **train_url**

#. When creating a training job, configure the input and output paths.

   Select an OBS path or dataset path as the training input, and an OBS path for the output.

Editing Training Code and Saving the Model
------------------------------------------

Training code and the code for saving the model are closely related to the AI engine you use. The following uses the TensorFlow framework as an example. Before starting this case study, you must `download <https://storage.googleapis.com/tensorflow/tf-keras-datasets/mnist.npz>`__ the **mnist.npz** file and upload it to the OBS bucket. The training input is the OBS path where the **mnist.npz** file is stored.

.. code-block::

   import os
   import argparse
   import tensorflow as tf

   parser = argparse.ArgumentParser(description='train mnist')
   parser.add_argument('--data_url', type=str, default="./Data/mnist.npz", help='path where the dataset is saved')
   parser.add_argument('--train_url', type=str, default="./Model", help='path where the model is saved')
   args = parser.parse_args()

   mnist = tf.keras.datasets.mnist

   (x_train, y_train), (x_test, y_test) = mnist.load_data(args.data_url)
   x_train, x_test = x_train / 255.0, x_test / 255.0

   model = tf.keras.models.Sequential([
       tf.keras.layers.Flatten(input_shape=(28, 28)),
       tf.keras.layers.Dense(128, activation='relu'),
       tf.keras.layers.Dropout(0.2),
       tf.keras.layers.Dense(10)
   ])

   loss_fn = tf.keras.losses.SparseCategoricalCrossentropy(from_logits=True)
   model.compile(optimizer='adam',
                 loss=loss_fn,
                 metrics=['accuracy'])
   model.fit(x_train, y_train, epochs=5)

   model.save(os.path.join(args.train_url, 'model'))

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
