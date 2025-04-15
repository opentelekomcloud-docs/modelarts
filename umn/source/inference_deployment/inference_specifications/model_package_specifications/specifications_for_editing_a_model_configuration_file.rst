:original_name: inference-modelarts-0056.html

.. _inference-modelarts-0056:

Specifications for Editing a Model Configuration File
=====================================================

You must edit a configuration file **config.json** when publishing a model. The model configuration file describes the model usage, computing framework, precision, inference code dependency package, and model API.

Configuration File Format
-------------------------

The configuration file is in JSON format. :ref:`Table 1 <en-us_topic_0000002268821749__en-us_topic_0172466149_table7143191919436>` describes the parameters.

.. _en-us_topic_0000002268821749__en-us_topic_0172466149_table7143191919436:

.. table:: **Table 1** Parameters

   +-----------------+-----------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                  | Description                                                                                                                                                                                                                                                                                                                                    |
   +=================+=================+=======================+================================================================================================================================================================================================================================================================================================================================================+
   | model_algorithm | Yes             | String                | Model algorithm, which is set by the model developer to help users understand the usage of the model. The value must start with a letter and contain no more than 36 characters. Special characters\ ``(&!'\"<>=)`` are not allowed. Common model algorithms include **image_classification**, **object_detection**, and **predict_analysis**. |
   +-----------------+-----------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | model_type      | Yes             | String                | Model AI engine, which indicates the computing framework used by a model. Common AI engines and **Image** are supported.                                                                                                                                                                                                                       |
   |                 |                 |                       |                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                       | -  For details about supported AI engines, see :ref:`Supported AI Engines for ModelArts Inference <en-us_topic_0000002079103881__en-us_topic_0171858287_section04192617912>`.                                                                                                                                                                  |
   |                 |                 |                       | -  If **model_type** is set to **Image**, the AI application is created using a custom image. In this case, parameter **swr_location** is mandatory. For details about specifications for custom images, see :ref:`Custom Image Specifications for Creating an AI Application <modelarts_23_0219>`.                                            |
   +-----------------+-----------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | runtime         | No              | String                | Model runtime environment. Python 3.6 is used by default. The value of **runtime** depends on the value of **model_type**. If **model_type** is set to **Image**, you do not need to set **runtime**. If **model_type** is set to another mainstream framework, select the engine and runtime environment.                                     |
   +-----------------+-----------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | swr_location    | No              | String                | SWR image address.                                                                                                                                                                                                                                                                                                                             |
   |                 |                 |                       |                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                       | -  If you import a custom image metamodel from a container image, you do not need to set **swr_location**.                                                                                                                                                                                                                                     |
   |                 |                 |                       | -  If you import a custom image meta model from OBS (not recommended) and set **model_type** to **Image**, you must set **swr_location**. **swr_location** specifies the path to the Docker image on SWR, which will be used to publish the model.                                                                                             |
   +-----------------+-----------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | metrics         | No              | Object                | Model precision information, including the F1 score, recall, precision, and accuracy. For details about the **metrics** object structure, see :ref:`Table 2 <en-us_topic_0000002079182513__en-us_topic_0172466149_table81712704511>`.                                                                                                          |
   |                 |                 |                       |                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                       | The result is displayed in the model precision area on the AI application details page.                                                                                                                                                                                                                                                        |
   +-----------------+-----------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | apis            | No              | api array             | Format of the requests received and returned by a model. The value is structure data.                                                                                                                                                                                                                                                          |
   |                 |                 |                       |                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                       | It is the RESTful API array provided by a model. For details about the API data structure, see :ref:`Table 3 <en-us_topic_0000002079182513__en-us_topic_0172466149_table1683418482455>`. For details about the code example, see :ref:`Code Example of apis Parameters <en-us_topic_0000002079182513__section9498141310396>`.                  |
   |                 |                 |                       |                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                       | -  If **model_type** is set to **Image**, the AI application is created using a custom image. APIs with different paths can be declared in **apis** based on the request path exposed by the image.                                                                                                                                            |
   |                 |                 |                       | -  When **model_type** is not **Image**, only one API whose request path is **/** can be declared in **apis** because the preconfigured AI engine exposes only one inference API whose request path is **/**.                                                                                                                                  |
   +-----------------+-----------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dependencies    | No              | dependency array      | Package on which the model inference code depends, which is structure data.                                                                                                                                                                                                                                                                    |
   |                 |                 |                       |                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                       | Model developers need to provide the package name, installation mode, and version constraints. Only the pip installation mode is supported. :ref:`Table 6 <en-us_topic_0000002079182513__en-us_topic_0172466149_table13709813144819>` describes the dependency array.                                                                          |
   |                 |                 |                       |                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                       | If the model package does not contain the **customize_service.py** file, you do not need to set this parameter. Dependency packages cannot be installed for custom image models.                                                                                                                                                               |
   +-----------------+-----------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | health          | No              | health data structure | Configuration of an image health interface. This parameter is mandatory only when **model_type** is set to **Image**.                                                                                                                                                                                                                          |
   |                 |                 |                       |                                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                       | If services cannot be interrupted during a rolling upgrade, a health check API must be provided for ModelArts to call. For details about the health data structure, see :ref:`Table 8 <en-us_topic_0000002079182513__en-us_topic_0172466149_table115896191852>`.                                                                               |
   +-----------------+-----------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002079182513__en-us_topic_0172466149_table81712704511:

.. table:: **Table 2** **metrics** object description

   +-----------+-----------+--------+-------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                           |
   +===========+===========+========+=======================================================+
   | f1        | No        | Number | F1 score. The value is rounded to 17 decimal places.  |
   +-----------+-----------+--------+-------------------------------------------------------+
   | recall    | No        | Number | Recall. The value is rounded to 17 decimal places.    |
   +-----------+-----------+--------+-------------------------------------------------------+
   | precision | No        | Number | Precision. The value is rounded to 17 decimal places. |
   +-----------+-----------+--------+-------------------------------------------------------+
   | accuracy  | No        | Number | Accuracy. The value is rounded to 17 decimal places.  |
   +-----------+-----------+--------+-------------------------------------------------------+

.. _en-us_topic_0000002268821749__en-us_topic_0172466149_table1683418482455:

.. table:: **Table 3** **api** data structure description

   +-----------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                                                                                                                                                                |
   +===========+===========+========+============================================================================================================================================================================================================================================================================+
   | url       | No        | String | Request path. The default value is a slash (**/**). For a custom image model (**model_type** is **Image**), set this parameter to the actual request path exposed in the image. For a non-custom image model (**model_type** is not **Image**), the URL can only be **/**. |
   +-----------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | method    | No        | String | Request method. The default value is **POST**.                                                                                                                                                                                                                             |
   +-----------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | request   | No        | Object | Request body. For details, see :ref:`Table 4 <en-us_topic_0000002268821749__en-us_topic_0172466149_table332913335466>`.                                                                                                                                                    |
   +-----------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | response  | No        | Object | Response body. For details, see :ref:`Table 5 <en-us_topic_0000002268821749__en-us_topic_0172466149_table17521240184711>`.                                                                                                                                                 |
   +-----------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002268821749__en-us_topic_0172466149_table332913335466:

.. table:: **Table 4** **request** structure description

   +-----------------+---------------------------+-----------------+----------------------------------------------------------------------------------------+
   | Parameter       | Mandatory                 | Type            | Description                                                                            |
   +=================+===========================+=================+========================================================================================+
   | Content-type    | No for real-time services | String          | Data is sent in a specified content format. The default value is **application/json**. |
   |                 |                           |                 |                                                                                        |
   |                 | Yes for batch services    |                 | The options are as follows:                                                            |
   |                 |                           |                 |                                                                                        |
   |                 |                           |                 | -  **application/json**: JSON data is uploaded.                                        |
   |                 |                           |                 | -  **multipart/form-data**: A file is uploaded.                                        |
   |                 |                           |                 |                                                                                        |
   |                 |                           |                 | .. note::                                                                              |
   |                 |                           |                 |                                                                                        |
   |                 |                           |                 |    For machine learning models, only **application/json** is supported.                |
   +-----------------+---------------------------+-----------------+----------------------------------------------------------------------------------------+
   | data            | No for real-time services | String          | The request body is described in JSON schema.                                          |
   |                 |                           |                 |                                                                                        |
   |                 | Yes for batch services    |                 |                                                                                        |
   +-----------------+---------------------------+-----------------+----------------------------------------------------------------------------------------+

.. _en-us_topic_0000002268821749__en-us_topic_0172466149_table17521240184711:

.. table:: **Table 5** **response** structure description

   +-----------------+---------------------------+-----------------+----------------------------------------------------------------------------------------+
   | Parameter       | Mandatory                 | Type            | Description                                                                            |
   +=================+===========================+=================+========================================================================================+
   | Content-type    | No for real-time services | String          | Data is sent in a specified content format. The default value is **application/json**. |
   |                 |                           |                 |                                                                                        |
   |                 | Yes for batch services    |                 | .. note::                                                                              |
   |                 |                           |                 |                                                                                        |
   |                 |                           |                 |    For machine learning models, only **application/json** is supported.                |
   +-----------------+---------------------------+-----------------+----------------------------------------------------------------------------------------+
   | data            | No for real-time services | String          | The response body is described in JSON schema.                                         |
   |                 |                           |                 |                                                                                        |
   |                 | Yes for batch services    |                 |                                                                                        |
   +-----------------+---------------------------+-----------------+----------------------------------------------------------------------------------------+

.. _en-us_topic_0000002268821749__en-us_topic_0172466149_table13709813144819:

.. table:: **Table 6** **dependency** array description

   +-----------+-----------+-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type              | Description                                                                                                                                                               |
   +===========+===========+===================+===========================================================================================================================================================================+
   | installer | Yes       | String            | Installation method. Only **pip** is supported.                                                                                                                           |
   +-----------+-----------+-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | packages  | Yes       | **package** array | Dependency package collection. For details about the package structure array, see :ref:`Table 7 <en-us_topic_0000002268821749__en-us_topic_0172466149_table47885356482>`. |
   +-----------+-----------+-------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002268821749__en-us_topic_0172466149_table47885356482:

.. table:: **Table 7** **package** array description

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                         |
   +=================+=================+=================+=====================================================================================================================================================================================+
   | package_name    | Yes             | String          | Dependency package name. Special characters\ ``(&!'"<>=)`` are not allowed.                                                                                                         |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | package_version | No              | String          | Dependency package version. If the dependency package does not rely on package versions, leave this field blank. Special characters\ ``(&!'"<>=)`` are not allowed.                 |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | restraint       | No              | String          | Version restriction. This parameter is mandatory only when **package_version** is configured. Possible values are **EXACT**, **ATLEAST**, and **ATMOST**.                           |
   |                 |                 |                 |                                                                                                                                                                                     |
   |                 |                 |                 | -  **EXACT** indicates that a specified version is installed.                                                                                                                       |
   |                 |                 |                 | -  **ATLEAST** indicates that the version of the installation package is not earlier than the specified version.                                                                    |
   |                 |                 |                 | -  **ATMOST** indicates that the version of the installation package is not later than the specified version.                                                                       |
   |                 |                 |                 |                                                                                                                                                                                     |
   |                 |                 |                 |    .. note::                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                     |
   |                 |                 |                 |       -  If there are specific requirements on the version, preferentially use **EXACT**. If **EXACT** conflicts with the system installation packages, you can select **ATLEAST**. |
   |                 |                 |                 |       -  If there is no specific requirement on the version, retain only the **package_name** parameter and leave **restraint** and **package_version** blank.                      |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002268821749__en-us_topic_0172466149_table115896191852:

.. table:: **Table 8** **health** data structure description

   +-----------------------+-----------+--------+------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory | Type   | Description                                                                                                |
   +=======================+===========+========+============================================================================================================+
   | url                   | Yes       | String | Request URL of the health check API.                                                                       |
   +-----------------------+-----------+--------+------------------------------------------------------------------------------------------------------------+
   | protocol              | No        | String | Request protocol of the health check API. Only HTTP is supported.                                          |
   +-----------------------+-----------+--------+------------------------------------------------------------------------------------------------------------+
   | initial_delay_seconds | No        | String | After an instance is started, a health check starts after seconds configured in **initial_delay_seconds**. |
   +-----------------------+-----------+--------+------------------------------------------------------------------------------------------------------------+
   | timeout_seconds       | No        | String | Health check timeout duration in the unit of second. This parameter cannot be left blank.                  |
   +-----------------------+-----------+--------+------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002268821749__section9498141310396:

Code Example of apis Parameters
-------------------------------

.. code-block::

   [{
       "url": "/",
       "method": "post",
       "request": {
           "Content-type": "multipart/form-data",
           "data": {
               "type": "object",
               "properties": {
                   "images": {
                       "type": "file"
                   }
               }
           }
       },
       "response": {
           "Content-type": "applicaton/json",
           "data": {
               "type": "object",
               "properties": {
                   "mnist_result": {
                       "type": "array",
                       "item": [
                           {
                               "type": "string"
                           }
                       ]
                   }
               }
           }
       }
   }]

.. _en-us_topic_0000002268821749__en-us_topic_0172466149_section218715919415:

Example of an Object Detection Model Configuration File
-------------------------------------------------------

The following code uses the TensorFlow engine as an example. You can modify the **model_type** parameter based on the actual engine type.

-  Model input

   Key: images

   Value: image files

-  Model output

   ::

      {
          "detection_classes": [
              "face",
              "arm"
          ],
          "detection_boxes": [
              [
                  33.6,
                  42.6,
                  104.5,
                  203.4
              ],
              [
                  103.1,
                  92.8,
                  765.6,
                  945.7
              ]
          ],
          "detection_scores": [0.99, 0.73]
      }

-  Configuration file

   ::

      {
          "model_type": "TensorFlow",
          "model_algorithm": "object_detection",
          "metrics": {
              "f1": 0.345294,
              "accuracy": 0.462963,
              "precision": 0.338977,
              "recall": 0.351852
          },
          "apis": [{

              "url": "/",
              "method": "post",
              "request": {
                  "Content-type": "multipart/form-data",
                  "data": {
                      "type": "object",
                      "properties": {
                          "images": {
                              "type": "file"
                          }
                      }
                  }
              },
              "response": {
                  "Content-type": "application/json",
                  "data": {
                      "type": "object",
                      "properties": {
                          "detection_classes": {
                              "type": "array",
                              "items": [{
                                  "type": "string"
                              }]
                          },
                          "detection_boxes": {
                              "type": "array",
                              "items": [{
                                  "type": "array",
                                  "minItems": 4,
                                  "maxItems": 4,
                                  "items": [{
                                      "type": "number"
                                  }]
                              }]
                          },
                          "detection_scores": {
                              "type": "array",
                              "items": [{
                                  "type": "number"
                              }]
                          }
                      }
                  }
              }
          }],
          "dependencies": [{
              "installer": "pip",
              "packages": [{
                      "restraint": "EXACT",
                      "package_version": "1.15.0",
                      "package_name": "numpy"
                  },
                  {
                      "restraint": "EXACT",
                      "package_version": "5.2.0",
                      "package_name": "Pillow"
                  }
              ]
          }]
      }

Example of an Image Classification Model Configuration File
-----------------------------------------------------------

The following code uses the TensorFlow engine as an example. You can modify the **model_type** parameter based on the actual engine type.

-  Model input

   Key: images

   Value: image files

-  Model output

   ::

      {
          "predicted_label": "flower",
          "scores": [
             ["rose", 0.99],
             ["begonia", 0.01]
          ]
      }

-  Configuration file

   ::

      {
          "model_type": "TensorFlow",
          "model_algorithm": "image_classification",
          "metrics": {
              "f1": 0.345294,
              "accuracy": 0.462963,
              "precision": 0.338977,
              "recall": 0.351852
          },
          "apis": [{

              "url": "/",
              "method": "post",
              "request": {
                  "Content-type": "multipart/form-data",
                  "data": {
                      "type": "object",
                      "properties": {
                          "images": {
                              "type": "file"
                          }
                      }
                  }
              },
              "response": {
                  "Content-type": "application/json",
                  "data": {
                      "type": "object",
                      "properties": {
                          "predicted_label": {
                              "type": "string"
                          },
                          "scores": {
                              "type": "array",
                              "items": [{
                                  "type": "array",
                                  "minItems": 2,
                                  "maxItems": 2,
                                  "items": [
                                      {
                                          "type": "string"
                                      },
                                      {
                                          "type": "number"
                                      }
                                  ]
                              }]
                          }
                      }
                  }
              }
          }],
          "dependencies": [{
              "installer": "pip",
              "packages": [{
                      "restraint": "ATLEAST",
                      "package_version": "1.15.0",
                      "package_name": "numpy"
                  },
                  {
                      "restraint": "",
                      "package_version": "",
                      "package_name": "Pillow"
                  }
              ]
          }]
      }

Example of a Predictive Analytics Model Configuration File
----------------------------------------------------------

The following code uses the TensorFlow engine as an example. You can modify the **model_type** parameter based on the actual engine type.

-  Model input

   ::

      {
          "data": {
              "req_data": [
                  {
                      "buying_price": "high",
                      "maint_price": "high",
                      "doors": "2",
                      "persons": "2",
                      "lug_boot": "small",
                      "safety": "low",
                      "acceptability": "acc"
                  },
                  {
                      "buying_price": "high",
                      "maint_price": "high",
                      "doors": "2",
                      "persons": "2",
                      "lug_boot": "small",
                      "safety": "low",
                      "acceptability": "acc"
                  }
              ]
          }
      }

-  Model output

   ::

      {
          "data": {
              "resp_data": [
                  {
                      "predict_result": "unacc"
                  },
                  {
                      "predict_result": "unacc"
                  }
              ]
          }
      }

-  Configuration file

   .. note::

      In the code, the **data** parameter in the request and response structures is described in JSON Schema. The content in **data** and **properties** corresponds to the model input and output.

   ::

      {
          "model_type": "TensorFlow",
          "model_algorithm": "predict_analysis",
          "metrics": {
              "f1": 0.345294,
              "accuracy": 0.462963,
              "precision": 0.338977,
              "recall": 0.351852
          },
          "apis": [
              {

                  "url": "/",
                  "method": "post",
                  "request": {
                      "Content-type": "application/json",
                      "data": {
                          "type": "object",
                          "properties": {
                              "data": {
                                  "type": "object",
                                  "properties": {
                                      "req_data": {
                                          "items": [
                                              {
                                                  "type": "object",
                                                  "properties": {}
                                              }
                                          ],
                                          "type": "array"
                                      }
                                  }
                              }
                          }
                      }
                  },
                  "response": {
                      "Content-type": "application/json",
                      "data": {
                          "type": "object",
                          "properties": {
                              "data": {
                                  "type": "object",
                                  "properties": {
                                      "resp_data": {
                                          "type": "array",
                                          "items": [
                                              {
                                                  "type": "object",
                                                  "properties": {}
                                              }
                                          ]
                                      }
                                  }
                             }
                          }
                      }
                  }
              }
          ],
          "dependencies": [
              {
                  "installer": "pip",
                  "packages": [
                      {
                          "restraint": "EXACT",
                          "package_version": "1.15.0",
                          "package_name": "numpy"
                      },
                      {
                          "restraint": "EXACT",
                          "package_version": "5.2.0",
                          "package_name": "Pillow"
                      }
                  ]
              }
          ]
      }

Example of a Custom Image Model Configuration File
--------------------------------------------------

The model input and output are similar to those in :ref:`Example of an Object Detection Model Configuration File <en-us_topic_0000002268821749__en-us_topic_0172466149_section218715919415>`.

-  The following is a request example when the input is images.

   This is a model prediction request containing the parameter **images** with the parameter type of file is received. The file upload button is displayed on the inference page. You need to upload files for inference.

   ::

      {
          "Content-type": "multipart/form-data",
          "data": {
              "type": "object",
              "properties": {
                  "images": {
                      "type": "file"
                  }
              }
          }
      }

-  The following is a request example when the input is JSON data.

   This is a JSON request body for model prediction. There is only one prediction request containing the parameter **input** with the parameter type of string. On the inference page, a text box is displayed for you to enter the prediction request.

   ::

      {
          "Content-type": "application/json",
          "data": {
              "type": "object",
              "properties": {
                  "input": {
                      "type": "string"
                  }
              }
          }
      }

A complete request example is as follows:

::

   {
       "model_algorithm": "image_classification",
       "model_type": "Image",
       "metrics": {
           "f1": 0.345294,
           "accuracy": 0.462963,
           "precision": 0.338977,
           "recall": 0.351852
       },
       "apis": [{

           "url": "/",
           "method": "post",
           "request": {
               "Content-type": "multipart/form-data",
               "data": {
                   "type": "object",
                   "properties": {
                       "images": {
                           "type": "file"
                       }
                   }
               }
           },
           "response": {
               "Content-type": "application/json",
               "data": {
                   "type": "object",
                   "required": [
                       "predicted_label",
                       "scores"
                   ],
                   "properties": {
                       "predicted_label": {
                           "type": "string"
                       },
                       "scores": {
                           "type": "array",
                           "items": [{
                               "type": "array",
                               "minItems": 2,
                               "maxItems": 2,
                               "items": [{
                                       "type": "string"
                                   },
                                   {
                                       "type": "number"
                                   }
                               ]
                           }]
                       }
                   }
               }
           }
       }]
   }

Example of a Machine Learning Model Configuration File
------------------------------------------------------

The following uses XGBoost as an example:

-  Model input

.. code-block::

   {
       "req_data": [
           {
               "sepal_length": 5,
               "sepal_width": 3.3,
               "petal_length": 1.4,
               "petal_width": 0.2
           },
           {
               "sepal_length": 5,
               "sepal_width": 2,
               "petal_length": 3.5,
               "petal_width": 1
           },
           {
               "sepal_length": 6,
               "sepal_width": 2.2,
               "petal_length": 5,
               "petal_width": 1.5
           }
       ]
   }

-  Model output

.. code-block::

   {
       "resp_data": [
           {
               "predict_result": "Iris-setosa"
           },
           {
               "predict_result": "Iris-versicolor"
           }
       ]
   }

-  Configuration file

.. code-block::

   {
       "model_type": "XGBoost",
       "model_algorithm": "xgboost_iris_test",
       "runtime": "python2.7",
       "metrics": {
           "f1": 0.345294,
           "accuracy": 0.462963,
           "precision": 0.338977,
           "recall": 0.351852
       },
       "apis": [
           {

               "url": "/",
               "method": "post",
               "request": {
                   "Content-type": "application/json",
                   "data": {
                       "type": "object",
                       "properties": {
                           "req_data": {
                               "items": [
                                   {
                                       "type": "object",
                                       "properties": {}
                                   }
                               ],
                               "type": "array"
                           }
                       }
                   }
               },
               "response": {
                   "Content-type": "applicaton/json",
                   "data": {
                       "type": "object",
                       "properties": {
                           "resp_data": {
                               "type": "array",
                               "items": [
                                   {
                                       "type": "object",
                                       "properties": {
                                           "predict_result": {}
                                       }
                                   }
                               ]
                           }
                       }
                   }
               }
           }
       ]
   }

.. _en-us_topic_0000002268821749__en-us_topic_0172466149_section119911955122011:

Example of a Model Configuration File Using a Custom Dependency Package
-----------------------------------------------------------------------

The following example defines the NumPy 1.16.4 dependency environment.

::

   {
       "model_algorithm": "image_classification",
       "model_type": "TensorFlow",
       "runtime": "python3.6",
       "apis": [
           {
               "procotol": "http",
               "url": "/",
               "method": "post",
               "request": {
                   "Content-type": "multipart/form-data",
                   "data": {
                       "type": "object",
                       "properties": {
                           "images": {
                               "type": "file"
                           }
                       }
                   }
               },
               "response": {
                   "Content-type": "applicaton/json",
                   "data": {
                       "type": "object",
                       "properties": {
                           "mnist_result": {
                               "type": "array",
                               "item": [
                                   {
                                       "type": "string"
                                   }
                               ]
                           }
                       }
                   }
               }
           }
       ],
       "metrics": {
           "f1": 0.124555,
           "recall": 0.171875,
           "precision": 0.00234938928519385,
           "accuracy": 0.00746268656716417
       },
       "dependencies": [
           {
               "installer": "pip",
               "packages": [
                   {
                       "restraint": "EXACT",
                       "package_version": "1.16.4",
                       "package_name": "numpy"
                   }
               ]
           }
       ]
   }
