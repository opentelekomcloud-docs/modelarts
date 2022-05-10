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

   +-----------------------------------+-------------------------------------------------------------------------------+
   | ::                                | ::                                                                            |
   |                                   |                                                                               |
   |     1                             |    from PIL import Image                                                      |
   |     2                             |    import numpy as np                                                         |
   |     3                             |    from model_service.tfserving_model_service import TfServingBaseService     |
   |     4                             |                                                                               |
   |     5                             |    class mnist_service(TfServingBaseService):                                 |
   |     6                             |                                                                               |
   |     7                             |        def _preprocess(self, data):                                           |
   |     8                             |            preprocessed_data = {}                                             |
   |     9                             |                                                                               |
   |    10                             |            for k, v in data.items():                                          |
   |    11                             |                for file_name, file_content in v.items():                      |
   |    12                             |                    image1 = Image.open(file_content)                          |
   |    13                             |                    image1 = np.array(image1, dtype=np.float32)                |
   |    14                             |                    image1.resize((1, 784))                                    |
   |    15                             |                    preprocessed_data[k] = image1                              |
   |    16                             |                                                                               |
   |    17                             |            return preprocessed_data                                           |
   |    18                             |                                                                               |
   |    19                             |        def _postprocess(self, data):                                          |
   |    20                             |                                                                               |
   |    21                             |            infer_output = {}                                                  |
   |    22                             |                                                                               |
   |    23                             |            for output_name, result in data.items():                           |
   |    24                             |                                                                               |
   |    25                             |                infer_output["mnist_result"] = result[0].index(max(result[0])) |
   |    26                             |                                                                               |
   |    27                             |            return infer_output                                                |
   +-----------------------------------+-------------------------------------------------------------------------------+

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

+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------+
| ::                                | ::                                                                                                                       |
|                                   |                                                                                                                          |
|      1                            |    # -*- coding: utf-8 -*-                                                                                               |
|      2                            |    import json                                                                                                           |
|      3                            |    import os                                                                                                             |
|      4                            |    import threading                                                                                                      |
|      5                            |                                                                                                                          |
|      6                            |    import numpy as np                                                                                                    |
|      7                            |    import tensorflow as tf                                                                                               |
|      8                            |    from PIL import Image                                                                                                 |
|      9                            |                                                                                                                          |
|     10                            |    from model_service.tfserving_model_service import TfServingBaseService                                                |
|     11                            |    import logging                                                                                                        |
|     12                            |                                                                                                                          |
|     13                            |    logger = logging.getLogger(__name__)                                                                                  |
|     14                            |                                                                                                                          |
|     15                            |                                                                                                                          |
|     16                            |    class MnistService(TfServingBaseService):                                                                             |
|     17                            |                                                                                                                          |
|     18                            |        def __init__(self, model_name, model_path):                                                                       |
|     19                            |            self.model_name = model_name                                                                                  |
|     20                            |            self.model_path = model_path                                                                                  |
|     21                            |            self.model_inputs = {}                                                                                        |
|     22                            |            self.model_outputs = {}                                                                                       |
|     23                            |                                                                                                                          |
|     24                            |           # The label file can be loaded here and used in the post-processing function.                                  |
|     25                            |            # Directories for storing the label.txt file on OBS and in the model package                                  |
|     26                            |                                                                                                                          |
|     27                            |            # with open(os.path.join(self.model_path, 'label.txt')) as f:                                                 |
|     28                            |            #     self.label = json.load(f)                                                                               |
|     29                            |                                                                                                                          |
|     30                            |            # Load the model in saved_model format in non-blocking mode to prevent blocking timeout.                      |
|     31                            |            thread = threading.Thread(target=self.get_tf_sess)                                                            |
|     32                            |            thread.start()                                                                                                |
|     33                            |                                                                                                                          |
|     34                            |        def get_tf_sess(self):                                                                                            |
|     35                            |            # Load the model in saved_model format.                                                                       |
|     36                            |                                                                                                                          |
|     37                            |           # The session will be reused. Do not use the with statement.                                                   |
|     38                            |            sess = tf.Session(graph=tf.Graph())                                                                           |
|     39                            |            meta_graph_def = tf.saved_model.loader.load(sess, [tf.saved_model.tag_constants.SERVING], self.model_path)    |
|     40                            |            signature_defs = meta_graph_def.signature_def                                                                 |
|     41                            |                                                                                                                          |
|     42                            |            self.sess = sess                                                                                              |
|     43                            |                                                                                                                          |
|     44                            |            signature = []                                                                                                |
|     45                            |                                                                                                                          |
|     46                            |            # only one signature allowed                                                                                  |
|     47                            |            for signature_def in signature_defs:                                                                          |
|     48                            |                signature.append(signature_def)                                                                           |
|     49                            |            if len(signature) == 1:                                                                                       |
|     50                            |                model_signature = signature[0]                                                                            |
|     51                            |            else:                                                                                                         |
|     52                            |                logger.warning("signatures more than one, use serving_default signature")                                 |
|     53                            |                model_signature = tf.saved_model.signature_constants.DEFAULT_SERVING_SIGNATURE_DEF_KEY                    |
|     54                            |                                                                                                                          |
|     55                            |            logger.info("model signature: %s", model_signature)                                                           |
|     56                            |                                                                                                                          |
|     57                            |            for signature_name in meta_graph_def.signature_def[model_signature].inputs:                                   |
|     58                            |                tensorinfo = meta_graph_def.signature_def[model_signature].inputs[signature_name]                         |
|     59                            |                name = tensorinfo.name                                                                                    |
|     60                            |                op = self.sess.graph.get_tensor_by_name(name)                                                             |
|     61                            |                self.model_inputs[signature_name] = op                                                                    |
|     62                            |                                                                                                                          |
|     63                            |            logger.info("model inputs: %s", self.model_inputs)                                                            |
|     64                            |                                                                                                                          |
|     65                            |            for signature_name in meta_graph_def.signature_def[model_signature].outputs:                                  |
|     66                            |                tensorinfo = meta_graph_def.signature_def[model_signature].outputs[signature_name]                        |
|     67                            |                name = tensorinfo.name                                                                                    |
|     68                            |                op = self.sess.graph.get_tensor_by_name(name)                                                             |
|     69                            |                                                                                                                          |
|     70                            |                self.model_outputs[signature_name] = op                                                                   |
|     71                            |                                                                                                                          |
|     72                            |            logger.info("model outputs: %s", self.model_outputs)                                                          |
|     73                            |                                                                                                                          |
|     74                            |        def _preprocess(self, data):                                                                                      |
|     75                            |            # Two request modes using HTTPS                                                                               |
|     76                            |            # 1. The request in form-data file format is as follows: data = {"Request key value":{"File name":<File io>}} |
|     77                            |           # 2. Request in JSON format is as follows: data = json.loads("JSON body transferred by the API")               |
|     78                            |            preprocessed_data = {}                                                                                        |
|     79                            |                                                                                                                          |
|     80                            |            for k, v in data.items():                                                                                     |
|     81                            |                for file_name, file_content in v.items():                                                                 |
|     82                            |                    image1 = Image.open(file_content)                                                                     |
|     83                            |                    image1 = np.array(image1, dtype=np.float32)                                                           |
|     84                            |                    image1.resize((1, 28, 28))                                                                            |
|     85                            |                    preprocessed_data[k] = image1                                                                         |
|     86                            |                                                                                                                          |
|     87                            |            return preprocessed_data                                                                                      |
|     88                            |                                                                                                                          |
|     89                            |        def _inference(self, data):                                                                                       |
|     90                            |                                                                                                                          |
|     91                            |            feed_dict = {}                                                                                                |
|     92                            |            for k, v in data.items():                                                                                     |
|     93                            |                if k not in self.model_inputs.keys():                                                                     |
|     94                            |                    logger.error("input key %s is not in model inputs %s", k, list(self.model_inputs.keys()))             |
|     95                            |                    raise Exception("input key %s is not in model inputs %s" % (k, list(self.model_inputs.keys())))       |
|     96                            |                feed_dict[self.model_inputs[k]] = v                                                                       |
|     97                            |                                                                                                                          |
|     98                            |            result = self.sess.run(self.model_outputs, feed_dict=feed_dict)                                               |
|     99                            |            logger.info('predict result : ' + str(result))                                                                |
|    100                            |                                                                                                                          |
|    101                            |            return result                                                                                                 |
|    102                            |                                                                                                                          |
|    103                            |        def _postprocess(self, data):                                                                                     |
|    104                            |            infer_output = {"mnist_result": []}                                                                           |
|    105                            |            for output_name, results in data.items():                                                                     |
|    106                            |                                                                                                                          |
|    107                            |                for result in results:                                                                                    |
|    108                            |                    infer_output["mnist_result"].append(np.argmax(result))                                                |
|    109                            |                                                                                                                          |
|    110                            |            return infer_output                                                                                           |
|    111                            |                                                                                                                          |
|    112                            |        def __del__(self):                                                                                                |
|    113                            |            self.sess.close()                                                                                             |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------+
