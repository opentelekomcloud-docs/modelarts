:original_name: modelarts_21_0038.html

.. _modelarts_21_0038:

Using TensorFlow for Handwritten Digit Recognition
==================================================

This section describes how to use TensorFlow to recognize handwritten digits in images from an MNIST dataset on the ModelArts platform.

Before using the following sample, complete necessary operations. For details, see :ref:`Preparations <modelarts_21_0038__section51133584536>`. The following describes the process of using TensorFlow to recognize handwritten digits in images.

#. **:ref:`Preparing Data <modelarts_21_0038__section336312088>`**: Obtain the MNIST dataset and upload it to OBS.
#. **:ref:`Training a Model <modelarts_21_0038__section42320342266>`**: Use the TensorFlow framework to compile the model training script and create a training job for model training.
#. **:ref:`Importing a Model <modelarts_21_0038__section740614592308>`**: After training is complete, import the model to ModelArts.
#. **:ref:`Deploying a Service <modelarts_21_0038__section18653124916459>`**: Deploy the imported model as a real-time service.
#. **:ref:`Performing Prediction <modelarts_21_0038__section9961181112311>`**: Initiate a prediction request and obtain the prediction result.

.. _modelarts_21_0038__section51133584536:

Preparations
------------

-  Obtain the AK/SK of the account and configure the AK/SK in **Settings** of ModelArts. For details, see :ref:`Configuring Access Authorization (Global Configuration) <modelarts_08_0006>`.

-  You have created a bucket and folders in OBS for storing the sample dataset and model. In this example, create a bucket named **test-modelarts** and folders listed in :ref:`Table 1 <modelarts_21_0038__en-us_topic_0168474775_table2061005120337>`.

   For details about how to create an OBS bucket and folder, see `Creating a Bucket <https://docs.otc.t-systems.com/en-us/usermanual/obs/en-us_topic_0045853662.html>`__ and `Creating a Folder <https://docs.otc.t-systems.com/en-us/usermanual/obs/obs_03_0316.html>`__. Ensure that OBS and ModelArts are in the same region and belong to the same account.

   .. _modelarts_21_0038__en-us_topic_0168474775_table2061005120337:

   .. table:: **Table 1** Folder list

      +-----------------------------+----------------------------------------------------------------+
      | Folder                      | Function                                                       |
      +=============================+================================================================+
      | mnist/dataset-mnist         | Stores the dataset.                                            |
      +-----------------------------+----------------------------------------------------------------+
      | mnist/mnist-tensorflow-code | Stores the training script.                                    |
      +-----------------------------+----------------------------------------------------------------+
      | mnist/mnist-model           | Stores the model and prediction files outputted from training. |
      +-----------------------------+----------------------------------------------------------------+

.. _modelarts_21_0038__section336312088:

Preparing Data
--------------

Obtain the `MNIST dataset <http://yann.lecun.com/exdb/mnist/>`__. Upload the following dataset files to the **test-modelarts/mnist/dataset-mnist** directory listed in :ref:`Table 1 <modelarts_21_0038__en-us_topic_0168474775_table2061005120337>`.

-  **t10k-images-idx3-ubyte.gz**: validation set
-  **t10k-labels-idx1-ubyte.gz**: labels of the validation set
-  **train-images-idx3-ubyte.gz**: training set
-  **train-labels-idx1-ubyte.gz**: labels of the training set

.. _modelarts_21_0038__section42320342266:

Training a Model
----------------

After data is prepared, use TensorFlow to compile the training script code. ModelArts provides a code sample, **train_mnist_tf.py**. The following uses this sample to train a model.

#. Upload the training script :ref:`train_mnist_tf.py <modelarts_21_0038__section10371851514>` to the **test-modelarts/mnist/mnist-tensorflow-code** directory listed in :ref:`Table 1 <modelarts_21_0038__en-us_topic_0168474775_table2061005120337>`.

#. On the ModelArts management console, choose **Training Management > Training Jobs**, and click **Create** in the upper left corner.

#. On the **Create Training Job** page, set required parameters based on :ref:`Table 2 <modelarts_21_0038__table1374631816418>`.

   .. _modelarts_21_0038__table1374631816418:

   .. table:: **Table 2** Training job parameters

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                         |
      +===================================+=====================================================================================================================================================================================+
      | Name                              | The value is specified by the system by default. You can change the value based on the site requirements, for example, **trainjob-mnist**.                                          |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Algorithm Source                  | Select **frequently-used**.                                                                                                                                                         |
      |                                   |                                                                                                                                                                                     |
      |                                   | -  **AI Engine**: TensorFlow, TF-1.8.0-python2.7                                                                                                                                    |
      |                                   | -  **Code Directory**: Click **Select** and select the OBS directory where the training script is stored. Set this parameter to the upper-level directory of the training script.   |
      |                                   | -  **Boot File**: Click **Select** and select the training script **train_mnist_tf.py** in the code directory.                                                                      |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Data Source                       | Select **Data path** and then select the OBS path for storing the dataset, that is, the data storage path described in :ref:`Preparing Data <modelarts_21_0038__section336312088>`. |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Training Output Path              | Set this parameter to the OBS directory created in :ref:`Preparations <modelarts_21_0038__section51133584536>` for storing the trained model.                                       |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Running Parameter                 | Retain the default value. In this example, no other parameters need to be added.                                                                                                    |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Resource Pool                     | Select **Public resource pools**.                                                                                                                                                   |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Type                              | Select **CPU**.                                                                                                                                                                     |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Specifications                    | Select **CPU: 2 vCPUs \| 8 GiB**.                                                                                                                                                   |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Compute Nodes                     | Set this parameter to **1**.                                                                                                                                                        |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _modelarts_21_0038__fig67462018144112:

   .. figure:: /_static/images/en-us_image_0000001278010757.png
      :alt: **Figure 1** Basic information for creating a training job


      **Figure 1** Basic information for creating a training job

   .. _modelarts_21_0038__fig18746141811415:

   .. figure:: /_static/images/en-us_image_0000001277931129.png
      :alt: **Figure 2** Parameters for creating a training job


      **Figure 2** Parameters for creating a training job

   .. _modelarts_21_0038__fig774192913455:

   .. figure:: /_static/images/en-us_image_0000001233650798.png
      :alt: **Figure 3** Resource specifications selected for a training job


      **Figure 3** Resource specifications selected for a training job

#. Check the parameters of the training job and click **Create Now**.

#. On the **Training Jobs** page, when the training job status changes to **Running Success**, the model training is complete. If any exception occurs, click the job name to go to the job details page and view the training job logs.

   .. note::

      The training job may take more than 10 minutes to complete. If the training time exceeds a certain period (for example, one hour), manually stop it to release resources. Otherwise, the account balance may be insufficient, especially for the training job using GPUs.

.. _modelarts_21_0038__section740614592308:

Importing a Model
-----------------

After model training is complete, you can import the model to ModelArts and deploy the model as a real-time service. Before deploying a model, obtain :ref:`Inference Code (customize_service.py) <modelarts_21_0038__section868435781614>` and :ref:`Configuration File (config.json) <modelarts_21_0038__section655951611710>`. The inference code and configuration file are sample files provided by ModelArts.

#. Before deploying the model, upload the inference code and configuration file to the corresponding OBS path.

   In this example, the OBS path for saving the outputted model is **test-modelarts/mnist/mnist-model/model**. Therefore, the inference script and configuration file need to be uploaded to this directory.

   .. note::

      -  Upload the files after the training is complete.
      -  If :ref:`Training a Model <modelarts_21_0038__section42320342266>` fails, the training job will be executed for multiple times. In this case, different versions are generated. Directories of multiple versions are generated in the **mnist-model** directory, for example, **V0001** and **V0002**. Upload the inference script and configuration file to the **model** folder of the corresponding version based on the version of the training job, for example, **test-modelarts/mnist/mnist-model/V0002/model**.

#. On the ModelArts management console, choose **Model Management** > **Models** in the left navigation pane. On the **Models** page, click **Import**.

#. On the **Import Model** page, set required parameters shown in :ref:`Figure 4 <modelarts_21_0038__fig1391183516364>` and click **Create Now**.

   Set **Meta Model Source** to **OBS**. Set **Meta Model** to the path specified by **Training Output Path** in the training job.

   .. table:: **Table 3** Parameters for importing a model

      +-------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter               | Description                                                                                                                                                                                                                                                 |
      +=========================+=============================================================================================================================================================================================================================================================+
      | Name                    | Set the model name, for example, **model-mnist**.                                                                                                                                                                                                           |
      +-------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Meta Model Source       | Select **Training job**. Set **Training Job** and **Version** to the job and version created in the previous step. After a training job is selected, the configuration file and inference code in the corresponding directory are automatically identified. |
      +-------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Deployment Type         | Select **Real-time services**.                                                                                                                                                                                                                              |
      +-------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Configuration File      | The configuration file has been uploaded to the directory where the model is located. Therefore, the button is disabled by default.                                                                                                                         |
      +-------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Inference Code          | The inference code has been uploaded to the directory where the model is located. The path of the inference code is automatically displayed.                                                                                                                |
      +-------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter Configuration | Click the **POST** area to view the input and output parameters of the model.                                                                                                                                                                               |
      +-------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Runtime Dependency      | Runtime dependency of the model                                                                                                                                                                                                                             |
      +-------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Min. Inference Specs    | Minimum inference specifications. In this example, this parameter can be disabled.                                                                                                                                                                          |
      +-------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _modelarts_21_0038__fig1391183516364:

   .. figure:: /_static/images/en-us_image_0000001233970646.png
      :alt: **Figure 4** Importing a model


      **Figure 4** Importing a model

.. _modelarts_21_0038__section18653124916459:

Deploying a Service
-------------------

#. On the **Models** page, if the model status changes to **Normal**, the model has been imported successfully.

#. Click the down arrow next to a model name to unfold all versions of the model. Locate the target version, and choose **Deploy** > **Real-Time Services** in the **Operation** column to deploy the model as a real-time service.

   .. _modelarts_21_0038__fig84961522143919:

   .. figure:: /_static/images/en-us_image_0000001278010761.png
      :alt: **Figure 5** Model list


      **Figure 5** Model list

#. On the **Deploy** page that is displayed, set the parameters shown in :ref:`Figure 6 <modelarts_21_0038__fig3534111012408>`, click **Create Now**, and create the real-time service as prompted.

   .. _modelarts_21_0038__fig3534111012408:

   .. figure:: /_static/images/en-us_image_0000001277931133.png
      :alt: **Figure 6** Deploying a model


      **Figure 6** Deploying a model

   After the service deployment task is started, go to the **Real-Time Services** page and wait until the service is deployed. The service deployment takes a couple of minutes. When the service status changes to **Running**, the service is successfully deployed.

.. _modelarts_21_0038__section9961181112311:

Performing Prediction
---------------------

#. On the **Service Deployment > Real-Time Services** page, click the name of the real-time service to go to the service details page.

#. Click the **Prediction** tab, click **Upload** next to **Image File** to upload an image with a white handwritten digit on a black background, and click **Predict**.

   After the prediction is complete, the prediction result is displayed in the **Test Result** pane. According to the prediction result, the digit on the image is **1**.

   .. note::

      -  As specified in the inference code and configuration file, the size of the image used for prediction must be 28 x 28 pixels, and the image must contain white handwritten digits on a black background.
      -  You are advised not to use the images provided by the dataset. You can use the drawing tool provided by the Windows operating system to draw an image for prediction.

   .. _modelarts_21_0038__en-us_topic_0168474775_fig2049295319516:

   .. figure:: /_static/images/en-us_image_0000001233650802.png
      :alt: **Figure 7** Prediction results


      **Figure 7** Prediction results

#. If the model and real-time service are no longer required, you are advised to clear related resources.

   -  On the **Real-Time Services** page, choose **More** > **Stop** or **Delete** to stop or delete the created real-time service.
   -  On the **Model Management** page, choose **More** > **Delete** to delete the imported model.
   -  On the **Training Jobs** page, choose **More** > **Delete** to delete the finished training job.
   -  Go to OBS and delete the OBS bucket, folders, and files in this example.

.. _modelarts_21_0038__section10371851514:

Training Script (train_mnist_tf.py)
-----------------------------------

Copy the following code and name the code file **train_mnist_tf.py**. The code is a training script compiled based on the TensorFlow engine in Python.

+-----------------------------------+---------------------------------------------------------------------------------------------------------------+
| ::                                | ::                                                                                                            |
|                                   |                                                                                                               |
|     1                             |    from __future__ import absolute_import                                                                     |
|     2                             |    from __future__ import division                                                                            |
|     3                             |    from __future__ import print_function                                                                      |
|     4                             |                                                                                                               |
|     5                             |    import os                                                                                                  |
|     6                             |                                                                                                               |
|     7                             |    import tensorflow as tf                                                                                    |
|     8                             |    from tensorflow.examples.tutorials.mnist import input_data                                                 |
|     9                             |                                                                                                               |
|    10                             |    tf.flags.DEFINE_integer('max_steps', 1000, 'number of training iterations.')                               |
|    11                             |    tf.flags.DEFINE_string('data_url', '/home/jnn/nfs/mnist', 'dataset directory.')                            |
|    12                             |    tf.flags.DEFINE_string('train_url', '/home/jnn/temp/delete', 'saved model directory.')                     |
|    13                             |                                                                                                               |
|    14                             |    FLAGS = tf.flags.FLAGS                                                                                     |
|    15                             |                                                                                                               |
|    16                             |                                                                                                               |
|    17                             |    def main(*args):                                                                                           |
|    18                             |      # Train model                                                                                            |
|    19                             |      print('Training model...')                                                                               |
|    20                             |      mnist = input_data.read_data_sets(FLAGS.data_url, one_hot=True)                                          |
|    21                             |      sess = tf.InteractiveSession()                                                                           |
|    22                             |      serialized_tf_example = tf.placeholder(tf.string, name='tf_example')                                     |
|    23                             |      feature_configs = {'x': tf.FixedLenFeature(shape=[784], dtype=tf.float32),}                              |
|    24                             |      tf_example = tf.parse_example(serialized_tf_example, feature_configs)                                    |
|    25                             |      x = tf.identity(tf_example['x'], name='x')                                                               |
|    26                             |      y_ = tf.placeholder('float', shape=[None, 10])                                                           |
|    27                             |      w = tf.Variable(tf.zeros([784, 10]))                                                                     |
|    28                             |      b = tf.Variable(tf.zeros([10]))                                                                          |
|    29                             |      sess.run(tf.global_variables_initializer())                                                              |
|    30                             |      y = tf.nn.softmax(tf.matmul(x, w) + b, name='y')                                                         |
|    31                             |      cross_entropy = -tf.reduce_sum(y_ * tf.log(y))                                                           |
|    32                             |                                                                                                               |
|    33                             |      tf.summary.scalar('cross_entropy', cross_entropy)                                                        |
|    34                             |                                                                                                               |
|    35                             |      train_step = tf.train.GradientDescentOptimizer(0.01).minimize(cross_entropy)                             |
|    36                             |                                                                                                               |
|    37                             |      correct_prediction = tf.equal(tf.argmax(y, 1), tf.argmax(y_, 1))                                         |
|    38                             |      accuracy = tf.reduce_mean(tf.cast(correct_prediction, 'float'))                                          |
|    39                             |      tf.summary.scalar('accuracy', accuracy)                                                                  |
|    40                             |      merged = tf.summary.merge_all()                                                                          |
|    41                             |      test_writer = tf.summary.FileWriter(FLAGS.train_url, flush_secs=1)                                       |
|    42                             |                                                                                                               |
|    43                             |      for step in range(FLAGS.max_steps):                                                                      |
|    44                             |        batch = mnist.train.next_batch(50)                                                                     |
|    45                             |        train_step.run(feed_dict={x: batch[0], y_: batch[1]})                                                  |
|    46                             |        if step % 10 == 0:                                                                                     |
|    47                             |          summary, acc = sess.run([merged, accuracy], feed_dict={x: mnist.test.images, y_: mnist.test.labels}) |
|    48                             |          test_writer.add_summary(summary, step)                                                               |
|    49                             |          print('training accuracy is:', acc)                                                                  |
|    50                             |      print('Done training!')                                                                                  |
|    51                             |                                                                                                               |
|    52                             |      builder = tf.saved_model.builder.SavedModelBuilder(os.path.join(FLAGS.train_url, 'model'))               |
|    53                             |                                                                                                               |
|    54                             |      tensor_info_x = tf.saved_model.utils.build_tensor_info(x)                                                |
|    55                             |      tensor_info_y = tf.saved_model.utils.build_tensor_info(y)                                                |
|    56                             |                                                                                                               |
|    57                             |      prediction_signature = (                                                                                 |
|    58                             |          tf.saved_model.signature_def_utils.build_signature_def(                                              |
|    59                             |              inputs={'images': tensor_info_x},                                                                |
|    60                             |              outputs={'scores': tensor_info_y},                                                               |
|    61                             |              method_name=tf.saved_model.signature_constants.PREDICT_METHOD_NAME))                             |
|    62                             |                                                                                                               |
|    63                             |      builder.add_meta_graph_and_variables(                                                                    |
|    64                             |          sess, [tf.saved_model.tag_constants.SERVING],                                                        |
|    65                             |          signature_def_map={                                                                                  |
|    66                             |              'predict_images':                                                                                |
|    67                             |                  prediction_signature,                                                                        |
|    68                             |          },                                                                                                   |
|    69                             |          main_op=tf.tables_initializer(),                                                                     |
|    70                             |          strip_default_attrs=True)                                                                            |
|    71                             |                                                                                                               |
|    72                             |      builder.save()                                                                                           |
|    73                             |                                                                                                               |
|    74                             |      print('Done exporting!')                                                                                 |
|    75                             |                                                                                                               |
|    76                             |                                                                                                               |
|    77                             |    if __name__ == '__main__':                                                                                 |
|    78                             |      tf.app.run(main=main)                                                                                    |
+-----------------------------------+---------------------------------------------------------------------------------------------------------------+

.. _modelarts_21_0038__section868435781614:

Inference Code (customize_service.py)
-------------------------------------

Copy the following code and name the code file **customize_service.py**. The following inference code meets the ModelArts model package specifications.

+-----------------------------------+------------------------------------------------------------------------------------+
| ::                                | ::                                                                                 |
|                                   |                                                                                    |
|     1                             |    from PIL import Image                                                           |
|     2                             |    import numpy as np                                                              |
|     3                             |    from model_service.tfserving_model_service import TfServingBaseService          |
|     4                             |                                                                                    |
|     5                             |                                                                                    |
|     6                             |    class mnist_service(TfServingBaseService):                                      |
|     7                             |      def _preprocess(self, data):                                                  |
|     8                             |        preprocessed_data = {}                                                      |
|     9                             |                                                                                    |
|    10                             |        for k, v in data.items():                                                   |
|    11                             |          for file_name, file_content in v.items():                                 |
|    12                             |            image1 = Image.open(file_content)                                       |
|    13                             |            image1 = np.array(image1, dtype=np.float32)                             |
|    14                             |            image1.resize((1, 784))                                                 |
|    15                             |            preprocessed_data[k] = image1                                           |
|    16                             |                                                                                    |
|    17                             |        return preprocessed_data                                                    |
|    18                             |                                                                                    |
|    19                             |      def _postprocess(self, data):                                                 |
|    20                             |                                                                                    |
|    21                             |        outputs = {}                                                                |
|    22                             |        logits = data['scores'][0]                                                  |
|    23                             |        label = logits.index(max(logits))                                           |
|    24                             |        logits = ['%.3f' % logit for logit in logits]                               |
|    25                             |        outputs['predicted_label'] = str(label)                                     |
|    26                             |        label_list = [str(label) for label in list(range(10))]                      |
|    27                             |        scores = dict(zip(label_list, logits))                                      |
|    28                             |        scores = sorted(scores.items(), key=lambda item: item[1], reverse=True)[:5] |
|    29                             |        outputs['scores'] = scores                                                  |
|    30                             |                                                                                    |
|    31                             |        return outputs                                                              |
+-----------------------------------+------------------------------------------------------------------------------------+

.. _modelarts_21_0038__section655951611710:

Configuration File (config.json)
--------------------------------

Copy the following code and name the code file **config.json**. The configuration file meets the ModelArts model package specifications.

+-----------------------------------+------------------------------------------------------------+
| ::                                | ::                                                         |
|                                   |                                                            |
|     1                             |    {                                                       |
|     2                             |        "model_type":"TensorFlow",                          |
|     3                             |        "metrics":{                                         |
|     4                             |            "f1":0,                                         |
|     5                             |            "accuracy":0,                                   |
|     6                             |            "precision":0,                                  |
|     7                             |            "recall":0                                      |
|     8                             |        },                                                  |
|     9                             |        "dependencies":[                                    |
|    10                             |            {                                               |
|    11                             |                "installer":"pip",                          |
|    12                             |                "packages":[                                |
|    13                             |                    {                                       |
|    14                             |                        "restraint":"ATLEAST",              |
|    15                             |                        "package_version":"1.15.0",         |
|    16                             |                        "package_name":"numpy"              |
|    17                             |                    },                                      |
|    18                             |                    {                                       |
|    19                             |                        "restraint":"",                     |
|    20                             |                        "package_version":"",               |
|    21                             |                        "package_name":"h5py"               |
|    22                             |                    },                                      |
|    23                             |                    {                                       |
|    24                             |                        "restraint":"ATLEAST",              |
|    25                             |                        "package_version":"1.8.0",          |
|    26                             |                        "package_name":"tensorflow"         |
|    27                             |                    },                                      |
|    28                             |                    {                                       |
|    29                             |                        "restraint":"ATLEAST",              |
|    30                             |                        "package_version":"5.2.0",          |
|    31                             |                        "package_name":"Pillow"             |
|    32                             |                    }                                       |
|    33                             |                ]                                           |
|    34                             |            }                                               |
|    35                             |        ],                                                  |
|    36                             |        "model_algorithm":"image_classification",           |
|    37                             |        "apis":[                                            |
|    38                             |            {                                               |
|    39                             |                "procotol":"http",                          |
|    40                             |                "url":"/",                                  |
|    41                             |                "request":{                                 |
|    42                             |                    "Content-type":"multipart/form-data",   |
|    43                             |                    "data":{                                |
|    44                             |                        "type":"object",                    |
|    45                             |                        "properties":{                      |
|    46                             |                            "images":{                      |
|    47                             |                                "type":"file"               |
|    48                             |                            }                               |
|    49                             |                        }                                   |
|    50                             |                    }                                       |
|    51                             |                },                                          |
|    52                             |                "method":"post",                            |
|    53                             |                "response":{                                |
|    54                             |                    "Content-type":"multipart/form-data",   |
|    55                             |                    "data":{                                |
|    56                             |                        "required":[                        |
|    57                             |                            "predicted_label",              |
|    58                             |                            "scores"                        |
|    59                             |                        ],                                  |
|    60                             |                        "type":"object",                    |
|    61                             |                        "properties":{                      |
|    62                             |                            "predicted_label":{             |
|    63                             |                                "type":"string"             |
|    64                             |                            },                              |
|    65                             |                            "scores":{                      |
|    66                             |                                "items":{                   |
|    67                             |                                    "minItems":2,           |
|    68                             |                                    "items":[               |
|    69                             |                                        {                   |
|    70                             |                                            "type":"string" |
|    71                             |                                        },                  |
|    72                             |                                        {                   |
|    73                             |                                            "type":"number" |
|    74                             |                                        }                   |
|    75                             |                                    ],                      |
|    76                             |                                    "type":"array",         |
|    77                             |                                    "maxItems":2            |
|    78                             |                                },                          |
|    79                             |                                "type":"array"              |
|    80                             |                            }                               |
|    81                             |                        }                                   |
|    82                             |                    }                                       |
|    83                             |                }                                           |
|    84                             |            }                                               |
|    85                             |        ]                                                   |
|    86                             |    }                                                       |
+-----------------------------------+------------------------------------------------------------+
