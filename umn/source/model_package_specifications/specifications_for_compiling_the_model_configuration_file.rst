.. _modelarts_23_0092:

Specifications for Compiling the Model Configuration File
=========================================================

A model developer needs to compile a configuration file when publishing a model. The model configuration file describes the model usage, computing framework, precision, inference code dependency package, and model API.

Configuration File Format
-------------------------

The configuration file is in JSON format. :ref:`Table 1 <modelarts_23_0092__en-us_topic_0172466149_table7143191919436>` describes the parameters.

.. _modelarts_23_0092__en-us_topic_0172466149_table7143191919436:

.. table:: **Table 1** Parameters

   +-----------------+-----------------+---------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Data Type                 | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
   +=================+=================+===========================+=============================================================================================================================================================================================================================================================================================================================================================================================================================================================+
   | model_algorithm | Yes             | String                    | Model algorithm, which is set by the model developer to help model users understand the usage of the model. The value must start with a letter and contain no more than 36 characters. Chinese characters and special characters (&!'\"<>=) are not allowed. Common model algorithms include **image_classification** (image classification), **object_detection** (object detection), and **predict_analysis** (prediction analysis).                      |
   +-----------------+-----------------+---------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | model_type      | Yes             | String                    | Model AI engine, which indicates the computing framework used by a model. The options are **TensorFlow**, **MXNet**, **Spark_MLlib**, **Caffe**, **Scikit_Learn**, **XGBoost**, **PyTorch**, **MindSpore**, and **Image**.                                                                                                                                                                                                                                  |
   |                 |                 |                           |                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
   |                 |                 |                           | **Image** is not a common AI framework. When **model_type** is set to **Image**, a model is imported from a custom image. In this case, **swr_location** is mandatory. For details about how to make Image images, see :ref:`Custom Image Specifications <modelarts_23_0084>`.                                                                                                                                                                              |
   +-----------------+-----------------+---------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | runtime         | No              | String                    | Model runtime environment. Python 3.6 is used by default. The value of **runtime** depends on the value of **model_type**. If **model_type** is set to **Image**, you do not need to set **runtime**. If **model_type** is set to another frequently-used framework, select the engine and development environment. For details about the supported running environments, see :ref:`Table 1 <modelarts_23_0207__en-us_topic_0207629478_table108792813184>`. |
   |                 |                 |                           |                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
   |                 |                 |                           | If your model needs to run on a specified CPU or GPU, select the runtime based on the suffix information. If the runtime does not contain the CPU or GPU information, read the description of each runtime in :ref:`Table 1 <modelarts_23_0207__en-us_topic_0207629478_table108792813184>`.                                                                                                                                                                 |
   +-----------------+-----------------+---------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | swr_location    | No              | String                    | SWR image address.                                                                                                                                                                                                                                                                                                                                                                                                                                          |
   |                 |                 |                           |                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
   |                 |                 |                           | -  If you import a custom image model from a container image, you do not need to set **swr_location**.                                                                                                                                                                                                                                                                                                                                                      |
   |                 |                 |                           | -  If you import a custom image model from OBS (not recommended) and set **model_type** to **Image**, you must set **swr_location**. **swr_location** indicates the address of the Docker image on SWR, indicating that the Docker image on SWR is used to publish the model.                                                                                                                                                                               |
   +-----------------+-----------------+---------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | metrics         | No              | Object                    | Model precision information, including the average value, recall rate, precision, and accuracy. For details about the **metrics** object structure, see :ref:`Table 2 <modelarts_23_0092__en-us_topic_0172466149_table81712704511>`.                                                                                                                                                                                                                        |
   |                 |                 |                           |                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
   |                 |                 |                           | This parameter is used only to display model information and is optional.                                                                                                                                                                                                                                                                                                                                                                                   |
   +-----------------+-----------------+---------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | apis            | No              | api array                 | Format of the requests received and returned by a model. The value is structure data.                                                                                                                                                                                                                                                                                                                                                                       |
   |                 |                 |                           |                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
   |                 |                 |                           | It is the RESTful API array provided by a model. For details about the API data structure, see :ref:`Table 3 <modelarts_23_0092__en-us_topic_0172466149_table1683418482455>`.                                                                                                                                                                                                                                                                               |
   |                 |                 |                           |                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
   |                 |                 |                           | -  When **model_type** is set to **Image**, that is, in the model scenario of a custom image, APIs with different paths can be declared in **apis** based on the request path exposed by the image.                                                                                                                                                                                                                                                         |
   |                 |                 |                           | -  When **model_type** is not **Image**, only one API whose request path is **/** can be declared in **apis** because the preconfigured AI engine exposes only one inference API whose request path is **/**.                                                                                                                                                                                                                                               |
   +-----------------+-----------------+---------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dependencies    | No              | dependency array          | Package on which the model inference code depends, which is structure data.                                                                                                                                                                                                                                                                                                                                                                                 |
   |                 |                 |                           |                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
   |                 |                 |                           | Model developers need to provide the package name, installation mode, and version constraints. Only the pip installation mode is supported. :ref:`Table 6 <modelarts_23_0092__en-us_topic_0172466149_table13709813144819>` describes the dependency array.                                                                                                                                                                                                  |
   |                 |                 |                           |                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
   |                 |                 |                           | If the model package does not contain the **customize_service.py** file, you do not need to set this parameter. Dependency packages cannot be installed for custom image models.                                                                                                                                                                                                                                                                            |
   +-----------------+-----------------+---------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | health          | No              | **health** data structure | Configuration of an image health interface. This parameter is mandatory only when **model_type** is set to **Image**. For details about the health data structure, see :ref:`Table 8 <modelarts_23_0092__en-us_topic_0172466149_table115896191852>`.                                                                                                                                                                                                        |
   +-----------------+-----------------+---------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _modelarts_23_0092__en-us_topic_0172466149_table81712704511:

.. table:: **Table 2** **metrics** object description

   +-----------+-----------+-----------+---------------------------------------------------------+
   | Parameter | Mandatory | Data Type | Description                                             |
   +===========+===========+===========+=========================================================+
   | f1        | No        | Number    | F1 score. The value is rounded to 17 decimal places.    |
   +-----------+-----------+-----------+---------------------------------------------------------+
   | recall    | No        | Number    | Recall rate. The value is rounded to 17 decimal places. |
   +-----------+-----------+-----------+---------------------------------------------------------+
   | precision | No        | Number    | Precision. The value is rounded to 17 decimal places.   |
   +-----------+-----------+-----------+---------------------------------------------------------+
   | accuracy  | No        | Number    | Accuracy. The value is rounded to 17 decimal places.    |
   +-----------+-----------+-----------+---------------------------------------------------------+

.. _modelarts_23_0092__en-us_topic_0172466149_table1683418482455:

.. table:: **Table 3** **api** array

   +-----------+-----------+-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Data Type | Description                                                                                                                                                                                                                                                                                           |
   +===========+===========+===========+=======================================================================================================================================================================================================================================================================================================+
   | protocol  | No        | String    | Request protocol. The default value is **http**. Set the parameter value to **http** or **https** based on your custom image. For details about other parameter, see :ref:`Example of the Object Detection Model Configuration File <modelarts_23_0092__en-us_topic_0172466149_section218715919415>`. |
   +-----------+-----------+-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | url       | No        | String    | Request path. The default value is a slash (**/**). For a custom image model (**model_type** is **Image**), set this parameter to the actual request path exposed in the image. For a non-custom image model (**model_type** is not **Image**), the URL can only be **/**.                            |
   +-----------+-----------+-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | method    | No        | String    | Request method. The default value is **POST**.                                                                                                                                                                                                                                                        |
   +-----------+-----------+-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | request   | No        | Object    | Request body. For details about the **request** structure, see :ref:`Table 4 <modelarts_23_0092__en-us_topic_0172466149_table332913335466>`.                                                                                                                                                          |
   +-----------+-----------+-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | response  | No        | Object    | Response body. For details about the **response** structure, see :ref:`Table 5 <modelarts_23_0092__en-us_topic_0172466149_table17521240184711>`.                                                                                                                                                      |
   +-----------+-----------+-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _modelarts_23_0092__en-us_topic_0172466149_table332913335466:

.. table:: **Table 4** **request** description

   +-----------------+----------------------------+-----------------+----------------------------------------------------------------------------------------+
   | Parameter       | Mandatory                  | Data Type       | Description                                                                            |
   +=================+============================+=================+========================================================================================+
   | Content-type    | Yes for real-time services | String          | Data is sent in a specified content format. The default value is **application/json**. |
   |                 |                            |                 |                                                                                        |
   |                 | No for batch services      |                 | The options are as follows:                                                            |
   |                 |                            |                 |                                                                                        |
   |                 |                            |                 | -  **application/json**: sends JSON data.                                              |
   |                 |                            |                 | -  **multipart/form-data**: uploads a file.                                            |
   |                 |                            |                 |                                                                                        |
   |                 |                            |                 | .. note::                                                                              |
   |                 |                            |                 |                                                                                        |
   |                 |                            |                 |    For machine learning models, only **application/json** is supported.                |
   +-----------------+----------------------------+-----------------+----------------------------------------------------------------------------------------+
   | data            | Yes for real-time services | String          | The request body is described in JSON schema.                                          |
   |                 |                            |                 |                                                                                        |
   |                 | No for batch services      |                 |                                                                                        |
   +-----------------+----------------------------+-----------------+----------------------------------------------------------------------------------------+

.. _modelarts_23_0092__en-us_topic_0172466149_table17521240184711:

.. table:: **Table 5** **response** description

   +-----------------+----------------------------+-----------------+----------------------------------------------------------------------------------------+
   | Parameter       | Mandatory                  | Data Type       | Description                                                                            |
   +=================+============================+=================+========================================================================================+
   | Content-type    | Yes for real-time services | String          | Data is sent in a specified content format. The default value is **application/json**. |
   |                 |                            |                 |                                                                                        |
   |                 | No for batch services      |                 | The options are as follows:                                                            |
   |                 |                            |                 |                                                                                        |
   |                 |                            |                 | -  **application/json**: sends JSON data.                                              |
   |                 |                            |                 | -  **multipart/form-data**: uploads a file.                                            |
   |                 |                            |                 |                                                                                        |
   |                 |                            |                 | .. note::                                                                              |
   |                 |                            |                 |                                                                                        |
   |                 |                            |                 |    For machine learning models, only **application/json** is supported.                |
   +-----------------+----------------------------+-----------------+----------------------------------------------------------------------------------------+
   | data            | Yes for real-time services | String          | The response body is described in JSON schema.                                         |
   |                 |                            |                 |                                                                                        |
   |                 | No for batch services      |                 |                                                                                        |
   +-----------------+----------------------------+-----------------+----------------------------------------------------------------------------------------+

.. _modelarts_23_0092__en-us_topic_0172466149_table13709813144819:

.. table:: **Table 6** **dependency** array

   +-----------+-----------+---------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Data Type     | Description                                                                                                                                                    |
   +===========+===========+===============+================================================================================================================================================================+
   | installer | Yes       | String        | Installation method. Only **pip** is supported.                                                                                                                |
   +-----------+-----------+---------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | packages  | Yes       | package array | Dependency package collection. For details about the package structure array, see :ref:`Table 7 <modelarts_23_0092__en-us_topic_0172466149_table47885356482>`. |
   +-----------+-----------+---------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _modelarts_23_0092__en-us_topic_0172466149_table47885356482:

.. table:: **Table 7** package array

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                             |
   +=================+=================+=================+=========================================================================================================================================================================================+
   | package_name    | Yes             | String          | Dependency package name. Chinese characters and special characters (&!'"<>=) are not allowed.                                                                                           |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | package_version | No              | String          | Dependency package version. If the dependency package does not rely on the version number, leave this field blank. Chinese characters and special characters (&!'"<>=) are not allowed. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | restraint       | No              | String          | Version restriction. This parameter is mandatory only when **package_version** is configured. Possible values are **EXACT**, **ATLEAST**, and **ATMOST**.                               |
   |                 |                 |                 |                                                                                                                                                                                         |
   |                 |                 |                 | -  **EXACT** indicates that a specified version is installed.                                                                                                                           |
   |                 |                 |                 | -  **ATLEAST** indicates that the version of the installation package is not earlier than the specified version.                                                                        |
   |                 |                 |                 | -  **ATMOST** indicates that the version of the installation package is not later than the specified version.                                                                           |
   |                 |                 |                 |                                                                                                                                                                                         |
   |                 |                 |                 |    .. note::                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                         |
   |                 |                 |                 |       -  If there are specific requirements on the version, preferentially use **EXACT**. If **EXACT** conflicts with the system installation packages, you can select **ATLEAST**.     |
   |                 |                 |                 |       -  If there is no specific requirement on the version, retain only the **package_name** parameter and leave **restraint** and **package_version** blank.                          |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _modelarts_23_0092__en-us_topic_0172466149_table115896191852:

.. table:: **Table 8** **health** data structure description

   +-----------------------+-----------+--------+------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory | Type   | Description                                                                                                |
   +=======================+===========+========+============================================================================================================+
   | url                   | Yes       | String | Request URL of the health check interface                                                                  |
   +-----------------------+-----------+--------+------------------------------------------------------------------------------------------------------------+
   | protocol              | No        | String | Request protocol of the health check interface. Only HTTP is supported.                                    |
   +-----------------------+-----------+--------+------------------------------------------------------------------------------------------------------------+
   | initial_delay_seconds | No        | String | After an instance is started, a health check starts after seconds configured in **initial_delay_seconds**. |
   +-----------------------+-----------+--------+------------------------------------------------------------------------------------------------------------+
   | timeout_seconds       | No        | String | Health check timeout                                                                                       |
   +-----------------------+-----------+--------+------------------------------------------------------------------------------------------------------------+

.. _modelarts_23_0092__en-us_topic_0172466149_section218715919415:

Example of the Object Detection Model Configuration File
--------------------------------------------------------

The following code uses the TensorFlow engine as an example. You can modify the **model_type** parameter based on the actual engine type.

-  Model input

   Key: images

   Value: image files

-  Model output

   +-----------------------------------+-----------------------------------------+
   | ::                                | ::                                      |
   |                                   |                                         |
   |     1                             |    ```                                  |
   |     2                             |    {                                    |
   |     3                             |        "detection_classes": [           |
   |     4                             |            "face",                      |
   |     5                             |            "arm"                        |
   |     6                             |        ],                               |
   |     7                             |        "detection_boxes": [             |
   |     8                             |            [                            |
   |     9                             |                33.6,                    |
   |    10                             |                42.6,                    |
   |    11                             |                104.5,                   |
   |    12                             |                203.4                    |
   |    13                             |            ],                           |
   |    14                             |            [                            |
   |    15                             |                103.1,                   |
   |    16                             |                92.8,                    |
   |    17                             |                765.6,                   |
   |    18                             |                945.7                    |
   |    19                             |            ]                            |
   |    20                             |        ],                               |
   |    21                             |        "detection_scores": [0.99, 0.73] |
   |    22                             |    }                                    |
   |    23                             |    ```                                  |
   +-----------------------------------+-----------------------------------------+

-  Configuration file

   +-----------------------------------+-------------------------------------------------------+
   | ::                                | ::                                                    |
   |                                   |                                                       |
   |     1                             |    ```                                                |
   |     2                             |    {                                                  |
   |     3                             |        "model_type": "TensorFlow",                    |
   |     4                             |        "model_algorithm": "object_detection",         |
   |     5                             |        "metrics": {                                   |
   |     6                             |            "f1": 0.345294,                            |
   |     7                             |            "accuracy": 0.462963,                      |
   |     8                             |            "precision": 0.338977,                     |
   |     9                             |            "recall": 0.351852                         |
   |    10                             |        },                                             |
   |    11                             |        "apis": [{                                     |
   |    12                             |            "protocol": "http",                        |
   |    13                             |            "url": "/",                                |
   |    14                             |            "method": "post",                          |
   |    15                             |            "request": {                               |
   |    16                             |                "Content-type": "multipart/form-data", |
   |    17                             |                "data": {                              |
   |    18                             |                    "type": "object",                  |
   |    19                             |                    "properties": {                    |
   |    20                             |                        "images": {                    |
   |    21                             |                            "type": "file"             |
   |    22                             |                        }                              |
   |    23                             |                    }                                  |
   |    24                             |                }                                      |
   |    25                             |            },                                         |
   |    26                             |            "response": {                              |
   |    27                             |                "Content-type": "multipart/form-data", |
   |    28                             |                "data": {                              |
   |    29                             |                    "type": "object",                  |
   |    30                             |                    "properties": {                    |
   |    31                             |                        "detection_classes": {         |
   |    32                             |                            "type": "array",           |
   |    33                             |                            "items": [{                |
   |    34                             |                                "type": "string"       |
   |    35                             |                            }]                         |
   |    36                             |                        },                             |
   |    37                             |                        "detection_boxes": {           |
   |    38                             |                            "type": "array",           |
   |    39                             |                            "items": [{                |
   |    40                             |                                "type": "array",       |
   |    41                             |                                "minItems": 4,         |
   |    42                             |                                "maxItems": 4,         |
   |    43                             |                                "items": [{            |
   |    44                             |                                    "type": "number"   |
   |    45                             |                                }]                     |
   |    46                             |                            }]                         |
   |    47                             |                        },                             |
   |    48                             |                        "detection_scores": {          |
   |    49                             |                            "type": "array",           |
   |    50                             |                            "items": [{                |
   |    51                             |                                "type": "number"       |
   |    52                             |                            }]                         |
   |    53                             |                        }                              |
   |    54                             |                    }                                  |
   |    55                             |                }                                      |
   |    56                             |            }                                          |
   |    57                             |        }],                                            |
   |    58                             |        "dependencies": [{                             |
   |    59                             |            "installer": "pip",                        |
   |    60                             |            "packages": [{                             |
   |    61                             |                    "restraint": "EXACT",              |
   |    62                             |                    "package_version": "1.15.0",       |
   |    63                             |                    "package_name": "numpy"            |
   |    64                             |                },                                     |
   |    65                             |                {                                      |
   |    66                             |                    "restraint": "EXACT",              |
   |    67                             |                    "package_version": "5.2.0",        |
   |    68                             |                    "package_name": "Pillow"           |
   |    69                             |                }                                      |
   |    70                             |            ]                                          |
   |    71                             |        }]                                             |
   |    72                             |    }                                                  |
   |    73                             |    ```                                                |
   +-----------------------------------+-------------------------------------------------------+

Example of the Image Classification Model Configuration File
------------------------------------------------------------

The following code uses the TensorFlow engine as an example. You can modify the **model_type** parameter based on the actual engine type.

-  Model input

   Key: images

   Value: image files

-  Model output

   +-----------------------------------+-------------------------------------+
   | ::                                | ::                                  |
   |                                   |                                     |
   |    1                              |    ```                              |
   |    2                              |    {                                |
   |    3                              |        "predicted_label": "flower", |
   |    4                              |        "scores": [                  |
   |    5                              |           ["rose", 0.99],           |
   |    6                              |           ["begonia", 0.01]         |
   |    7                              |        ]                            |
   |    8                              |    }                                |
   |    9                              |    ```                              |
   +-----------------------------------+-------------------------------------+

-  Configuration file

   +-----------------------------------+---------------------------------------------------------+
   | ::                                | ::                                                      |
   |                                   |                                                         |
   |     1                             |    ```                                                  |
   |     2                             |    {                                                    |
   |     3                             |        "model_type": "TensorFlow",                      |
   |     4                             |        "model_algorithm": "image_classification",       |
   |     5                             |        "metrics": {                                     |
   |     6                             |            "f1": 0.345294,                              |
   |     7                             |            "accuracy": 0.462963,                        |
   |     8                             |            "precision": 0.338977,                       |
   |     9                             |            "recall": 0.351852                           |
   |    10                             |        },                                               |
   |    11                             |        "apis": [{                                       |
   |    12                             |            "protocol": "http",                          |
   |    13                             |            "url": "/",                                  |
   |    14                             |            "method": "post",                            |
   |    15                             |            "request": {                                 |
   |    16                             |                "Content-type": "multipart/form-data",   |
   |    17                             |                "data": {                                |
   |    18                             |                    "type": "object",                    |
   |    19                             |                    "properties": {                      |
   |    20                             |                        "images": {                      |
   |    21                             |                            "type": "file"               |
   |    22                             |                        }                                |
   |    23                             |                    }                                    |
   |    24                             |                }                                        |
   |    25                             |            },                                           |
   |    26                             |            "response": {                                |
   |    27                             |                "Content-type": "multipart/form-data",   |
   |    28                             |                "data": {                                |
   |    29                             |                    "type": "object",                    |
   |    30                             |                    "properties": {                      |
   |    31                             |                        "predicted_label": {             |
   |    32                             |                            "type": "string"             |
   |    33                             |                        },                               |
   |    34                             |                        "scores": {                      |
   |    35                             |                            "type": "array",             |
   |    36                             |                            "items": [{                  |
   |    37                             |                                "type": "array",         |
   |    38                             |                                "minItems": 2,           |
   |    39                             |                                "maxItems": 2,           |
   |    40                             |                                "items": [               |
   |    41                             |                                    {                    |
   |    42                             |                                        "type": "string" |
   |    43                             |                                    },                   |
   |    44                             |                                    {                    |
   |    45                             |                                        "type": "number" |
   |    46                             |                                    }                    |
   |    47                             |                                ]                        |
   |    48                             |                            }]                           |
   |    49                             |                        }                                |
   |    50                             |                    }                                    |
   |    51                             |                }                                        |
   |    52                             |            }                                            |
   |    53                             |        }],                                              |
   |    54                             |        "dependencies": [{                               |
   |    55                             |            "installer": "pip",                          |
   |    56                             |            "packages": [{                               |
   |    57                             |                    "restraint": "ATLEAST",              |
   |    58                             |                    "package_version": "1.15.0",         |
   |    59                             |                    "package_name": "numpy"              |
   |    60                             |                },                                       |
   |    61                             |                {                                        |
   |    62                             |                    "restraint": "",                     |
   |    63                             |                    "package_version": "",               |
   |    64                             |                    "package_name": "Pillow"             |
   |    65                             |                }                                        |
   |    66                             |            ]                                            |
   |    67                             |        }]                                               |
   |    68                             |    }                                                    |
   |    69                             |    ```                                                  |
   +-----------------------------------+---------------------------------------------------------+

Example of the Predictive Analytics Model Configuration File
------------------------------------------------------------

The following code uses the TensorFlow engine as an example. You can modify the **model_type** parameter based on the actual engine type.

-  Model input

   +-----------------------------------+--------------------------------------------+
   | ::                                | ::                                         |
   |                                   |                                            |
   |     1                             |    ```                                     |
   |     2                             |    {                                       |
   |     3                             |        "data": {                           |
   |     4                             |            "req_data": [                   |
   |     5                             |                {                           |
   |     6                             |                    "buying_price": "high", |
   |     7                             |                    "maint_price": "high",  |
   |     8                             |                    "doors": "2",           |
   |     9                             |                    "persons": "2",         |
   |    10                             |                    "lug_boot": "small",    |
   |    11                             |                    "safety": "low",        |
   |    12                             |                    "acceptability": "acc"  |
   |    13                             |                },                          |
   |    14                             |                {                           |
   |    15                             |                    "buying_price": "high", |
   |    16                             |                    "maint_price": "high",  |
   |    17                             |                    "doors": "2",           |
   |    18                             |                    "persons": "2",         |
   |    19                             |                    "lug_boot": "small",    |
   |    20                             |                    "safety": "low",        |
   |    21                             |                    "acceptability": "acc"  |
   |    22                             |                }                           |
   |    23                             |            ]                               |
   |    24                             |        }                                   |
   |    25                             |    }                                       |
   |    26                             |    ```                                     |
   +-----------------------------------+--------------------------------------------+

-  Model output

   +-----------------------------------+----------------------------------------------+
   | ::                                | ::                                           |
   |                                   |                                              |
   |     1                             |    ```                                       |
   |     2                             |    {                                         |
   |     3                             |        "data": {                             |
   |     4                             |            "resp_data": [                    |
   |     5                             |                {                             |
   |     6                             |                    "predict_result": "unacc" |
   |     7                             |                },                            |
   |     8                             |                {                             |
   |     9                             |                    "predict_result": "unacc" |
   |    10                             |                }                             |
   |    11                             |            ]                                 |
   |    12                             |        }                                     |
   |    13                             |    }                                         |
   |    14                             |    ```                                       |
   +-----------------------------------+----------------------------------------------+

-  Configuration file

   +-----------------------------------+------------------------------------------------------------------+
   | ::                                | ::                                                               |
   |                                   |                                                                  |
   |     1                             |    ```                                                           |
   |     2                             |    {                                                             |
   |     3                             |        "model_type": "TensorFlow",                               |
   |     4                             |        "model_algorithm": "predict_analysis",                    |
   |     5                             |        "metrics": {                                              |
   |     6                             |            "f1": 0.345294,                                       |
   |     7                             |            "accuracy": 0.462963,                                 |
   |     8                             |            "precision": 0.338977,                                |
   |     9                             |            "recall": 0.351852                                    |
   |    10                             |        },                                                        |
   |    11                             |        "apis": [                                                 |
   |    12                             |            {                                                     |
   |    13                             |                "protocol": "http",                               |
   |    14                             |                "url": "/",                                       |
   |    15                             |                "method": "post",                                 |
   |    16                             |                "request": {                                      |
   |    17                             |                    "Content-type": "application/json",           |
   |    18                             |                    "data": {                                     |
   |    19                             |                        "type": "object",                         |
   |    20                             |                        "properties": {                           |
   |    21                             |                            "data": {                             |
   |    22                             |                                "type": "object",                 |
   |    23                             |                                "properties": {                   |
   |    24                             |                                    "req_data": {                 |
   |    25                             |                                        "items": [                |
   |    26                             |                                            {                     |
   |    27                             |                                                "type": "object", |
   |    28                             |                                                "properties": {   |
   |    29                             |                                                }                 |
   |    30                             |                                            }],                   |
   |    31                             |                                        "type": "array"           |
   |    32                             |                                    }                             |
   |    33                             |                                }                                 |
   |    34                             |                            }                                     |
   |    35                             |                        }                                         |
   |    36                             |                    }                                             |
   |    37                             |                },                                                |
   |    38                             |                "response": {                                     |
   |    39                             |                    "Content-type": "multipart/form-data",        |
   |    40                             |                    "data": {                                     |
   |    41                             |                        "type": "object",                         |
   |    42                             |                        "properties": {                           |
   |    43                             |                            "data": {                             |
   |    44                             |                                "type": "object",                 |
   |    45                             |                                "properties": {                   |
   |    46                             |                                    "resp_data": {                |
   |    47                             |                                        "type": "array",          |
   |    48                             |                                        "items": [                |
   |    49                             |                                            {                     |
   |    50                             |                                                "type": "object", |
   |    51                             |                                                "properties": {   |
   |    52                             |                                                }                 |
   |    53                             |                                            }]                    |
   |    54                             |                                    }                             |
   |    55                             |                                }                                 |
   |    56                             |                            }                                     |
   |    57                             |                        }                                         |
   |    58                             |                    }                                             |
   |    59                             |                }                                                 |
   |    60                             |            }],                                                   |
   |    61                             |        "dependencies": [                                         |
   |    62                             |            {                                                     |
   |    63                             |                "installer": "pip",                               |
   |    64                             |                "packages": [                                     |
   |    65                             |                    {                                             |
   |    66                             |                        "restraint": "EXACT",                     |
   |    67                             |                        "package_version": "1.15.0",              |
   |    68                             |                        "package_name": "numpy"                   |
   |    69                             |                    },                                            |
   |    70                             |                    {                                             |
   |    71                             |                        "restraint": "EXACT",                     |
   |    72                             |                        "package_version": "5.2.0",               |
   |    73                             |                        "package_name": "Pillow"                  |
   |    74                             |                    }]                                            |
   |    75                             |            }]                                                    |
   |    76                             |    }                                                             |
   |    77                             |    ```                                                           |
   +-----------------------------------+------------------------------------------------------------------+

.. _modelarts_23_0092__en-us_topic_0172466149_section9113122232018:

Example of the Custom Image Model Configuration File
----------------------------------------------------

The model input and output are similar to those in :ref:`Example of the Object Detection Model Configuration File <modelarts_23_0092__en-us_topic_0172466149_section218715919415>`.

+-----------------------------------+---------------------------------------------------------+
| ::                                | ::                                                      |
|                                   |                                                         |
|     1                             |    {                                                    |
|     2                             |        "model_algorithm": "image_classification",       |
|     3                             |        "model_type": "Image",                           |
|     4                             |                                                         |
|     5                             |        "metrics": {                                     |
|     6                             |            "f1": 0.345294,                              |
|     7                             |            "accuracy": 0.462963,                        |
|     8                             |            "precision": 0.338977,                       |
|     9                             |            "recall": 0.351852                           |
|    10                             |        },                                               |
|    11                             |        "apis": [{                                       |
|    12                             |            "protocol": "http",                          |
|    13                             |            "url": "/",                                  |
|    14                             |            "method": "post",                            |
|    15                             |            "request": {                                 |
|    16                             |                "Content-type": "multipart/form-data",   |
|    17                             |                "data": {                                |
|    18                             |                    "type": "object",                    |
|    19                             |                    "properties": {                      |
|    20                             |                        "images": {                      |
|    21                             |                            "type": "file"               |
|    22                             |                        }                                |
|    23                             |                    }                                    |
|    24                             |                }                                        |
|    25                             |            },                                           |
|    26                             |            "response": {                                |
|    27                             |                "Content-type": "multipart/form-data",   |
|    28                             |                "data": {                                |
|    29                             |                    "type": "object",                    |
|    30                             |                    "required": [                        |
|    31                             |                        "predicted_label",               |
|    32                             |                        "scores"                         |
|    33                             |                    ],                                   |
|    34                             |                    "properties": {                      |
|    35                             |                        "predicted_label": {             |
|    36                             |                            "type": "string"             |
|    37                             |                        },                               |
|    38                             |                        "scores": {                      |
|    39                             |                            "type": "array",             |
|    40                             |                            "items": [{                  |
|    41                             |                                "type": "array",         |
|    42                             |                                "minItems": 2,           |
|    43                             |                                "maxItems": 2,           |
|    44                             |                                "items": [{              |
|    45                             |                                        "type": "string" |
|    46                             |                                    },                   |
|    47                             |                                    {                    |
|    48                             |                                        "type": "number" |
|    49                             |                                    }                    |
|    50                             |                                ]                        |
|    51                             |                            }]                           |
|    52                             |                        }                                |
|    53                             |                    }                                    |
|    54                             |                }                                        |
|    55                             |            }                                            |
|    56                             |        }]                                               |
|    57                             |    }                                                    |
+-----------------------------------+---------------------------------------------------------+

Example of the Machine Learning Model Configuration File
--------------------------------------------------------

The following uses XGBoost as an example:

-  Model input

.. code-block::

   {
       "data": {
           "req_data": [{
               "sepal_length": 5,
               "sepal_width": 3.3,
               "petal_length": 1.4,
               "petal_width": 0.2
           }, {
               "sepal_length": 5,
               "sepal_width": 2,
               "petal_length": 3.5,
               "petal_width": 1
           }, {
               "sepal_length": 6,
               "sepal_width": 2.2,
               "petal_length": 5,
               "petal_width": 1.5
           }]
       }
   }

-  Model output

.. code-block::

   {
       "data": {
           "resp_data": [{
               "predict_result": "Iris-setosa"
           }, {
               "predict_result": "Iris-versicolor"
           }]
       }
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
         "protocol": "http",
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
                       "predict_result": {
                         "type": "number"
                       }
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

.. _modelarts_23_0092__en-us_topic_0172466149_section119911955122011:

Example of a Model Configuration File Using a Custom Dependency Package
-----------------------------------------------------------------------

The following example defines the NumPy 1.16.4 dependency environment.

+-----------------------------------+------------------------------------------------------------+
| ::                                | ::                                                         |
|                                   |                                                            |
|     1                             |    {                                                       |
|     2                             |         "model_algorithm": "image_classification",         |
|     3                             |         "model_type": "TensorFlow",                        |
|     4                             |         "runtime": "python3.6",                            |
|     5                             |         "apis": [{                                         |
|     6                             |                 "procotol": "http",                        |
|     7                             |                 "url": "/",                                |
|     8                             |                 "method": "post",                          |
|     9                             |                 "request": {                               |
|    10                             |                     "Content-type": "multipart/form-data", |
|    11                             |                     "data": {                              |
|    12                             |                         "type": "object",                  |
|    13                             |                         "properties": {                    |
|    14                             |                             "images": {                    |
|    15                             |                                 "type": "file"             |
|    16                             |                             }                              |
|    17                             |                         }                                  |
|    18                             |                     }                                      |
|    19                             |                 },                                         |
|    20                             |                 "response": {                              |
|    21                             |                     "Content-type": "applicaton/json",     |
|    22                             |                     "data": {                              |
|    23                             |                         "type": "object",                  |
|    24                             |                         "properties": {                    |
|    25                             |                             "mnist_result": {              |
|    26                             |                                 "type": "array",           |
|    27                             |                 "item": [{                                 |
|    28                             |                    "type": "string"                        |
|    29                             |                             }]                             |
|    30                             |                             }                              |
|    31                             |                         }                                  |
|    32                             |                     }                                      |
|    33                             |                 }                                          |
|    34                             |             }                                              |
|    35                             |         ],                                                 |
|    36                             |         "metrics": {                                       |
|    37                             |             "f1": 0.124555,                                |
|    38                             |             "recall": 0.171875,                            |
|    39                             |             "precision": 0.0023493892851938493,            |
|    40                             |             "accuracy": 0.00746268656716417                |
|    41                             |         },                                                 |
|    42                             |        "dependencies": [{                                  |
|    43                             |            "installer": "pip",                             |
|    44                             |            "packages": [{                                  |
|    45                             |                    "restraint": "EXACT",                   |
|    46                             |                    "package_version": "1.16.4",            |
|    47                             |                    "package_name": "numpy"                 |
|    48                             |                }                                           |
|    49                             |            ]                                               |
|    50                             |        }]                                                  |
|    51                             |     }                                                      |
+-----------------------------------+------------------------------------------------------------+
