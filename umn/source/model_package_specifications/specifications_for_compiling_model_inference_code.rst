:original_name: modelarts_23_0093.html

.. _modelarts_23_0093:

Specifications for Compiling Model Inference Code
=================================================

This section describes how to compile model inference code in ModelArts. The following also provides an example of inference code for the TensorFlow engine and an example of customizing inference logic in an inference script.

Specifications for Compiling Inference Code
-------------------------------------------

#. All custom Python code must be inherited from the BaseService class. :ref:`Table 1 <modelarts_23_0093__en-us_topic_0172466150_table55021545175412>` lists the import statements of different types of model parent classes.

   .. _modelarts_23_0093__en-us_topic_0172466150_table55021545175412:

   .. table:: **Table 1** Import statements of the **BaseService** class

      +--------------+-------------------------+------------------------------------------------------------------------+
      | Model Type   | Parent Class            | Import Statement                                                       |
      +==============+=========================+========================================================================+
      | TensorFlow   | TfServingBaseService    | from model_service.tfserving_model_service import TfServingBaseService |
      +--------------+-------------------------+------------------------------------------------------------------------+
      | MXNet        | MXNetBaseService        | from mms.model_service.mxnet_model_service import MXNetBaseService     |
      +--------------+-------------------------+------------------------------------------------------------------------+
      | PyTorch      | PTServingBaseService    | from model_service.pytorch_model_service import PTServingBaseService   |
      +--------------+-------------------------+------------------------------------------------------------------------+
      | Pyspark      | SparkServingBaseService | from model_service.spark_model_service import SparkServingBaseService  |
      +--------------+-------------------------+------------------------------------------------------------------------+
      | Caffe        | CaffeBaseService        | from model_service.caffe_model_service import CaffeBaseService         |
      +--------------+-------------------------+------------------------------------------------------------------------+
      | XGBoost      | XgSklServingBaseService | from model_service.python_model_service import XgSklServingBaseService |
      +--------------+-------------------------+------------------------------------------------------------------------+
      | Scikit_Learn | XgSklServingBaseService | from model_service.python_model_service import XgSklServingBaseService |
      +--------------+-------------------------+------------------------------------------------------------------------+

#. The following methods can be rewritten:

   .. table:: **Table 2** Methods to be rewritten

      +-----------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Method                                  | Description                                                                                                                                                                                                                                              |
      +=========================================+==========================================================================================================================================================================================================================================================+
      | \__init__(self, model_name, model_path) | Initialization method, which is suitable for models created based on deep learning frameworks. Models and labels are loaded using this method. This method must be rewritten for models based on PyTorch and Caffe to implement the model loading logic. |
      +-----------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \__init__(self, model_path)             | Initialization method, which is suitable for models created based on machine learning frameworks. The model path (**self.model_path**) is initialized using this method. In Spark_MLlib, this method also initializes SparkSession (**self.spark**).     |
      +-----------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \_preprocess(self, data)                | Preprocess method, which is called before an inference request and is used to convert the original request data of an API into the expected input data of a model                                                                                        |
      +-----------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \_inference(self, data)                 | Inference request method. You are not advised to rewrite the method because once the method is rewritten, the built-in inference process of ModelArts will be overwritten and the custom inference logic will run.                                       |
      +-----------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | \_postprocess(self, data)               | Postprocess method, which is called after an inference request is complete and is used to convert the model output to the API output                                                                                                                     |
      +-----------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. note::

      -  You can choose to rewrite the preprocess and postprocess methods to implement preprocessing of the API input and postprocessing of the inference output.
      -  Rewriting the init method of the BaseService inheritance class may cause a model to run abnormally.

#. .. _modelarts_23_0093__en-us_topic_0172466150_li135956421288:

   The attribute that can be used is the local path where the model resides. The attribute name is **self.model_path**. In addition, PySpark-based models can use **self.spark** to obtain the SparkSession object in **customize_service.py**.

   .. note::

      An absolute path is required for reading files in the inference code. You can obtain the absolute path of the model from the **self.model_path** attribute.

      -  When TensorFlow, Caffe, or MXNet is used, **self.model_path** indicates the path of the model file. See the following example:

         .. code-block::

            # Store the label.json file in the model directory. The following information is read:
            with open(os.path.join(self.model_path, 'label.json')) as f:
                self.label = json.load(f)

      -  When PyTorch, Scikit_Learn, or PySpark is used, **self.model_path** indicates the path of the model file. See the following example:

         .. code-block::

            # Store the label.json file in the model directory. The following information is read:
            dir_path = os.path.dirname(os.path.realpath(self.model_path))
            with open(os.path.join(dir_path, 'label.json')) as f:
                self.label = json.load(f)

#. Two types of **content-type** APIs can be used for inputting data: **multipart/form-data** and **application/json**

   -  **multipart/form-data** request

      .. code-block::

         curl -X POST \
           <modelarts-inference-endpoint> \
           -F image1=@cat.jpg \
           -F images2=@horse.jpg

      The corresponding input data is as follows:

      .. code-block::

         [
            {
               "image1":{
                  "cat.jpg":"<cat..jpg file io>"
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

      The corresponding input data is **python dict**.

      .. code-block::

         {
             "images":"base64 encode image"

          }

TensorFlow Inference Script Example
-----------------------------------

The following is an example of TensorFlow MnistService.

-  Inference code

   .. code-block::

      from PIL import Image
      import numpy as np
      from model_service.tfserving_model_service import TfServingBaseService

      class mnist_service(TfServingBaseService):

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

The preceding code example resizes images imported to the user's form to adapt to the model input shape. The **32×32** image is read from the Pillow library and resized to **1×784** to match the model input. In subsequent processing, convert the model output into a list for the RESTful API to display.

XGBoost Inference Script Example
--------------------------------

.. code-block::

   # coding:utf-8
   import collections
   import json
   import xgboost as xgb
   from model_service.python_model_service import XgSklServingBaseService


   class user_Service(XgSklServingBaseService):

       # request data preprocess
       def _preprocess(self, data):
           list_data = []
           json_data = json.loads(data, object_pairs_hook=collections.OrderedDict)
           for element in json_data["data"]["req_data"]:
               array = []
               for each in element:
                   array.append(element[each])
                   list_data.append(array)
           return list_data

       #   predict
       def _inference(self, data):
           xg_model = xgb.Booster(model_file=self.model_path)
           pre_data = xgb.DMatrix(data)
           pre_result = xg_model.predict(pre_data)
           pre_result = pre_result.tolist()
           return pre_result

       # predict result process
       def _postprocess(self, data):
           resp_data = []
           for element in data:
               resp_data.append({"predict_result": element})
           return resp_data

Inference Script Example of the Custom Inference Logic
------------------------------------------------------

First, define a dependency package in the configuration file. For details, see :ref:`Example of a Model Configuration File Using a Custom Dependency Package <modelarts_23_0092__en-us_topic_0172466149_section119911955122011>`. Then, use the following code example to implement the loading and inference of the model in **saved_model** format.

.. code-block::

   # -*- coding: utf-8 -*-
   import json
   import os
   import threading

   import numpy as np
   import tensorflow as tf
   from PIL import Image

   from model_service.tfserving_model_service import TfServingBaseService
   import logging

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
           # 1. The request in form-data file format is as follows: data = {"Request key value":{"File name":<File io>}}
          # 2. Request in JSON format is as follows: data = json.loads("JSON body transferred by the API")
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
