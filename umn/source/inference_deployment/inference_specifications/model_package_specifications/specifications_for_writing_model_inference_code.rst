:original_name: inference-modelarts-0057.html

.. _inference-modelarts-0057:

Specifications for Writing Model Inference Code
===============================================

This section describes the general method of editing model inference code in ModelArts. This section also provides an inference code example for the TensorFlow engine and an example of customizing the inference logic in the inference script.

Due to the limitation of API Gateway, the duration of a single prediction in ModelArts cannot exceed 40s. The model inference code must be logically clear and concise for satisfactory inference performance.

Specifications for Writing Inference Code
-----------------------------------------

#. In the model inference code file **customize_service.py**, add a child model class. This child model class inherits properties from its parent model class. For details about the import statements of different types of parent model classes, see :ref:`Table 1 <en-us_topic_0000002233742604__en-us_topic_0172466150_table55021545175412>`.

   .. _en-us_topic_0000002233742604__en-us_topic_0172466150_table55021545175412:

   .. table:: **Table 1** Import statements of different types of parent model classes

      +------------+----------------------+------------------------------------------------------------------------+
      | Model Type | Parent Class         | Import Statement                                                       |
      +============+======================+========================================================================+
      | TensorFlow | TfServingBaseService | from model_service.tfserving_model_service import TfServingBaseService |
      +------------+----------------------+------------------------------------------------------------------------+
      | PyTorch    | PTServingBaseService | from model_service.pytorch_model_service import PTServingBaseService   |
      +------------+----------------------+------------------------------------------------------------------------+
      | MindSpore  | SingleNodeService    | from model_service.model_service import SingleNodeService              |
      +------------+----------------------+------------------------------------------------------------------------+

#. The following methods can be overridden.

   .. table:: **Table 2** Methods to be overridden

      +-----------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Method                                  | Description                                                                                                                                                                                                                                               |
      +=========================================+===========================================================================================================================================================================================================================================================+
      | \__init__(self, model_name, model_path) | Initialization method, which is suitable for models created based on deep learning frameworks. Models and labels are loaded using this method. This method must be overridden for models based on PyTorch and Caffe to implement the model loading logic. |
      +-----------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \__init__(self, model_path)             | Initialization method, which is suitable for models created based on machine learning frameworks. This method initializes the model path (**self.model_path**). In Spark_MLlib, this method also initializes SparkSession (**self.spark**).               |
      +-----------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \_preprocess(self, data)                | Preprocess method, which is called before an inference request and is used to convert the original request data of an API into the expected input data of a model.                                                                                        |
      +-----------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \_inference(self, data)                 | Inference request method. You are advised not to override the method because once the method is overridden, the built-in inference process of ModelArts will be overwritten and the custom inference logic will run.                                      |
      +-----------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \_postprocess(self, data)               | Postprocess method, which is called after an inference request is complete and is used to convert the model output to the API output.                                                                                                                     |
      +-----------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. note::

      -  You can override the preprocess and postprocess methods for preprocessing the API input and postprocessing the inference output.
      -  Overriding the init method of the parent model class may cause a model to run abnormally.

#. .. _en-us_topic_0000002233742604__en-us_topic_0172466150_li135956421288:

   The attribute that can be used is the local path where the model resides. The attribute name is **self.model_path**. In addition, PySpark-based models can use **self.spark** to obtain the SparkSession object in **customize_service.py**.

   .. note::

      An absolute path is required for reading files in the inference code. You can obtain the local path of the model from the **self.model_path** attribute.

      -  When TensorFlow, Caffe, or MXNet is used, **self.model_path** indicates the path to the model file. The following provides an example:

         .. code-block::

            # Reads the label.json file in the model directory.
            with open(os.path.join(self.model_path, 'label.json')) as f:
                self.label = json.load(f)

      -  When PyTorch, Scikit_Learn, or PySpark is used, **self.model_path** indicates the path of the model file. The following provides an example:

         .. code-block::

            # Reads the label.json file in the model directory.
            dir_path = os.path.dirname(os.path.realpath(self.model_path))
            with open(os.path.join(dir_path, 'label.json')) as f:
                self.label = json.load(f)

#. **data** imported through the API for pre-processing, actual inference request, and post-processing can be **multipart/form-data** or **application/json**.

   -  **multipart/form-data** request

      .. code-block::

         curl -X POST \
           <modelarts-inference-endpoint> \
           -F image1=@cat.jpg \
           -F images2=@horse.jpg

      The input data is as follows:

      .. code-block::

         [
            {
               "image1":{
                  "cat.jpg":"<cat.jpg file io>"
               }
            },
            {
               "image2":{
                  "horse.jpg":"<horse.jpg file io>"
               }
            }
         ]

   -  **application/json** request

      .. code-block::

          curl -X POST \
            <modelarts-inference-endpoint> \
            -d '{
             "images":"base64 encode image"
             }'

      The input data is **python dict**.

      .. code-block::

          {
             "images":"base64 encode image"

          }

TensorFlow Inference Script Example
-----------------------------------

The following is an example of TensorFlow MnistService. For details about the inference code of other engines, see :ref:`PyTorch <inference-modelarts-0082>` and :ref:`Caffe <inference-modelarts-0083>`.

-  Inference code

   ::

      from PIL import Image
      import numpy as np
      from model_service.tfserving_model_service import TfServingBaseService

      class MnistService(TfServingBaseService):

          def _preprocess(self, data):
              preprocessed_data = {}

              for k, v in data.items():
                  for file_name, file_content in v.items():
                      image1 = Image.open(file_content)
                      image1 = np.array(image1, dtype=np.float32)
                      image1.resize((1, 784))
                      preprocessed_data[k] = image1

              return preprocessed_data

          def _postprocess(self, data):

              infer_output = {}

              for output_name, result in data.items():

                  infer_output["mnist_result"] = result[0].index(max(result[0]))

              return infer_output

-  Request

   .. code-block::

      curl -X POST \ Real-time service address \ -F images=@test.jpg

-  Response

   .. code-block::

      {"mnist_result": 7}

The preceding sample code resizes images imported to the user's form to adapt to the model input shape. The **32x32** image is read from the Pillow library and resized to **1x784** to match the model input. In subsequent processing, convert the model output into a list for the RESTful API to display.

Inference Script Example of Custom Inference Logic
--------------------------------------------------

Customize a dependency package in the configuration file by referring to :ref:`Example of a Model Configuration File Using a Custom Dependency Package <en-us_topic_0000002268821749__en-us_topic_0172466149_section119911955122011>`. Then, use the following code example to load the model in **saved_model** format for inference.

.. note::

   Python logging used by base inference images allows the display of only warning logs. To display INFO logs, set the log level to INFO in the code.

::

   # -*- coding: utf-8 -*-
   import json
   import os
   import threading

   import numpy as np
   import tensorflow as tf
   from PIL import Image

   from model_service.tfserving_model_service import TfServingBaseService
   import logging
   logging.basicConfig(level=logging.INFO, format='%(asctime)s - %(name)s - %(levelname)s - %(message)s')

   logger = logging.getLogger(__name__)


   class MnistService(TfServingBaseService):

       def __init__(self, model_name, model_path):
           self.model_name = model_name
           self.model_path = model_path
           self.model_inputs = {}
           self.model_outputs = {}

          # The label file can be loaded here and used in the post-processing function.
           # Directories for storing the label.txt file on OBS and in the model package

           # with open(os.path.join(self.model_path, 'label.txt')) as f:
           #     self.label = json.load(f)

           # Load the model in saved_model format in non-blocking mode to prevent blocking timeout.
           thread = threading.Thread(target=self.get_tf_sess)
           thread.start()

       def get_tf_sess(self):
           # Load the model in saved_model format.

          # The session will be reused. Do not use the with statement.
           sess = tf.Session(graph=tf.Graph())
           meta_graph_def = tf.saved_model.loader.load(sess, [tf.saved_model.tag_constants.SERVING], self.model_path)
           signature_defs = meta_graph_def.signature_def

           self.sess = sess

           signature = []

           # only one signature allowed
           for signature_def in signature_defs:
               signature.append(signature_def)
           if len(signature) == 1:
               model_signature = signature[0]
           else:
               logger.warning("signatures more than one, use serving_default signature")
               model_signature = tf.saved_model.signature_constants.DEFAULT_SERVING_SIGNATURE_DEF_KEY

           logger.info("model signature: %s", model_signature)

           for signature_name in meta_graph_def.signature_def[model_signature].inputs:
               tensorinfo = meta_graph_def.signature_def[model_signature].inputs[signature_name]
               name = tensorinfo.name
               op = self.sess.graph.get_tensor_by_name(name)
               self.model_inputs[signature_name] = op

           logger.info("model inputs: %s", self.model_inputs)

           for signature_name in meta_graph_def.signature_def[model_signature].outputs:
               tensorinfo = meta_graph_def.signature_def[model_signature].outputs[signature_name]
               name = tensorinfo.name
               op = self.sess.graph.get_tensor_by_name(name)

               self.model_outputs[signature_name] = op

           logger.info("model outputs: %s", self.model_outputs)

       def _preprocess(self, data):
           # Two request modes using HTTPS
           # 1. The request in form-data format is as follows: data = {"Request key value":{"File name":<File io>}}
           # 2. Request in JSON format is as follows: data = json.loads("JSON body passed in the API")
           preprocessed_data = {}

           for k, v in data.items():
               for file_name, file_content in v.items():
                   image1 = Image.open(file_content)
                   image1 = np.array(image1, dtype=np.float32)
                   image1.resize((1, 28, 28))
                   preprocessed_data[k] = image1

           return preprocessed_data

       def _inference(self, data):

           feed_dict = {}
           for k, v in data.items():
               if k not in self.model_inputs.keys():
                   logger.error("input key %s is not in model inputs %s", k, list(self.model_inputs.keys()))
                   raise Exception("input key %s is not in model inputs %s" % (k, list(self.model_inputs.keys())))
               feed_dict[self.model_inputs[k]] = v

           result = self.sess.run(self.model_outputs, feed_dict=feed_dict)
           logger.info('predict result : ' + str(result))

           return result

       def _postprocess(self, data):
           infer_output = {"mnist_result": []}
           for output_name, results in data.items():

               for result in results:
                   infer_output["mnist_result"].append(np.argmax(result))

           return infer_output

       def __del__(self):
           self.sess.close()

.. note::

   To load models that are not supported by ModelArts or multiple models, specify the loading path using the **\__init_\_** method. Example code is as follows:

   .. code-block::

      # -*- coding: utf-8 -*-
      import os
      from model_service.tfserving_model_service import TfServingBaseService

      class MnistService(TfServingBaseService):
          def __init__(self, model_name, model_path):
              # Obtain the path to the model folder.
              root = os.path.dirname(os.path.abspath(__file__))
              # test.onnx is the name of the model file to be loaded and must be stored in the model folder.
              self.model_path = os.path.join(root, test.onnx)

              # Loading multiple models, for example, test2.onnx
              # self.model_path2 = os.path.join(root, test2.onnx)

MindSpore Inference Script Example
----------------------------------

-  The inference script is as follows:

   .. code-block::

      import threading

      import mindspore
      import mindspore.nn as nn
      import numpy as np
      import logging
      from mindspore import Tensor, context
      from mindspore.common.initializer import Normal
      from mindspore.train.serialization import load_checkpoint, load_param_into_net
      from model_service.model_service import SingleNodeService
      from PIL import Image

      logger = logging.getLogger(__name__)
      logger.setLevel(logging.INFO)


      context.set_context(mode=context.GRAPH_MODE, device_target="Ascend")


      class LeNet5(nn.Cell):
          """Lenet network structure."""

          # define the operator required
          def __init__(self, num_class=10, num_channel=1):
              super(LeNet5, self).__init__()
              self.conv1 = nn.Conv2d(num_channel, 6, 5, pad_mode='valid')
              self.conv2 = nn.Conv2d(6, 16, 5, pad_mode='valid')
              self.fc1 = nn.Dense(16 * 5 * 5, 120, weight_init=Normal(0.02))
              self.fc2 = nn.Dense(120, 84, weight_init=Normal(0.02))
              self.fc3 = nn.Dense(84, num_class, weight_init=Normal(0.02))
              self.relu = nn.ReLU()
              self.max_pool2d = nn.MaxPool2d(kernel_size=2, stride=2)
              self.flatten = nn.Flatten()

          # use the preceding operators to construct networks
          def construct(self, x):
              x = self.max_pool2d(self.relu(self.conv1(x)))
              x = self.max_pool2d(self.relu(self.conv2(x)))
              x = self.flatten(x)
              x = self.relu(self.fc1(x))
              x = self.relu(self.fc2(x))
              x = self.fc3(x)
              return x


      class MnistService(SingleNodeService):
          def __init__(self, model_name, model_path):
              self.model_name = model_name
              self.model_path = model_path
              logger.info("self.model_name:%s self.model_path: %s", self.model_name,
                          self.model_path)
              self.network = None
              # Load the model in non-blocking mode to prevent blocking timeout.
              thread = threading.Thread(target=self.load_model)
              thread.start()

          def load_model(self):
              logger.info("load network ... \n")
              self.network = LeNet5()
              ckpt_file = self.model_path + "/checkpoint_lenet_1-1_1875.ckpt"
              logger.info("ckpt_file: %s", ckpt_file)
              param_dict = load_checkpoint(ckpt_file)
              load_param_into_net(self.network, param_dict)
              # Inference warm-up. Otherwise, the initial inference will take a long time.
              self.network_warmup()
              logger.info("load network successfully ! \n")

          def network_warmup(self):
              # Inference warm-up. Otherwise, the initial inference will take a long time.
              logger.info("warmup network ... \n")
              images = np.array(np.random.randn(1, 1, 32, 32), dtype=np.float32)
              inputs = Tensor(images, mindspore.float32)
              inference_result = self.network(inputs)
              logger.info("warmup network successfully ! \n")

          def _preprocess(self, input_data):
              preprocessed_result = {}
              images = []
              for k, v in input_data.items():
                  for file_name, file_content in v.items():
                      image1 = Image.open(file_content)
                      image1 = image1.resize((1, 32 * 32))
                      image1 = np.array(image1, dtype=np.float32)
                      images.append(image1)

              images = np.array(images, dtype=np.float32)
              logger.info(images.shape)
              images.resize([len(input_data), 1, 32, 32])
              logger.info("images shape: %s", images.shape)
              inputs = Tensor(images, mindspore.float32)
              preprocessed_result['images'] = inputs

              return preprocessed_result

          def _inference(self, preprocessed_result):
              inference_result = self.network(preprocessed_result['images'])
              return inference_result

          def _postprocess(self, inference_result):
              return str(inference_result)
