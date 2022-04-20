.. _modelarts_03_0056:

Querying a Built-in Algorithm
=============================

Function
--------

This API is used to query the details about a built-in model.

URI
---

GET /v1/{project_id}/built-in-algorithms

:ref:`Table 1 <modelarts_03_0056__en-us_topic_0131380352_table37435132101942>` describes the required parameters.

.. _modelarts_03_0056__en-us_topic_0131380352_table37435132101942:

.. table:: **Table 1** Parameters

   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                 |
   +============+===========+========+=============================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+

Request Body
------------

:ref:`Table 2 <modelarts_03_0056__en-us_topic_0131380352_table16279151181311>` describes the request parameters.

.. _modelarts_03_0056__en-us_topic_0131380352_table16279151181311:

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                     |
   +=================+=================+=================+=================================================================================================================================================================================================================+
   | per_page        | No              | Integer         | Number of job parameters displayed on each page. The value range is [1, 100]. Default value: **10**                                                                                                             |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | page            | No              | Integer         | Index of the page to be queried. Default value: **1**                                                                                                                                                           |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sortBy          | No              | String          | Sorting mode of the query. The value can be **engine**, **model_name**, **model_precision**, **model_usage**, **model_precision**, **model_size**, **create_time**, or **parameter**. Default value: **engine** |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | order           | No              | String          | Sorting order. The options are as follows:                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                 |
   |                 |                 |                 | -  **asc**: ascending order                                                                                                                                                                                     |
   |                 |                 |                 | -  **desc**: descending order. The default value is **desc**.                                                                                                                                                   |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | search_content  | No              | String          | Search content, for example, a parameter name. By default, this parameter is left blank.                                                                                                                        |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Body
-------------

:ref:`Table 3 <modelarts_03_0056__en-us_topic_0131380352_table10251721151647>` describes the response parameters.

.. _modelarts_03_0056__en-us_topic_0131380352_table10251721151647:

.. table:: **Table 3** Parameters

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                          |
   +=======================+=======================+======================================================================================================================================================+
   | is_success            | Boolean               | Whether the request is successful                                                                                                                    |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | error_message         | String                | Error message of a failed API call.                                                                                                                  |
   |                       |                       |                                                                                                                                                      |
   |                       |                       | This parameter is not included when the API call succeeds.                                                                                           |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | error_code            | String                | Error code of a failed API call. For details, see :ref:`Error Codes <modelarts_03_0095>`. This parameter is not included when the API call succeeds. |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | model_total_count     | Integer               | Number of models                                                                                                                                     |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | models                | Array<Object>         | Model parameter list. For details, see :ref:`Table 4 <modelarts_03_0056__en-us_topic_0131380352_table29182771151827>`.                               |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _modelarts_03_0056__en-us_topic_0131380352_table29182771151827:

.. table:: **Table 4** **models** structure data

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                     |
   +=======================+=======================+=================================================================================================================================================================+
   | model_id              | Integer               | Model ID                                                                                                                                                        |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | model_name            | String                | Model name                                                                                                                                                      |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | model_usage           | Integer               | Model usage. The options are as follows:                                                                                                                        |
   |                       |                       |                                                                                                                                                                 |
   |                       |                       | -  1: image classification                                                                                                                                      |
   |                       |                       | -  2: object class and location                                                                                                                                 |
   |                       |                       | -  3: image semantic segmentation                                                                                                                               |
   |                       |                       | -  4: natural language processing                                                                                                                               |
   |                       |                       | -  5: image embedding                                                                                                                                           |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | model_precision       | String                | Model precision                                                                                                                                                 |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | model_size            | Long                  | Model size, in bytes                                                                                                                                            |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | model_train_dataset   | String                | Model training dataset                                                                                                                                          |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | model_dataset_format  | String                | Dataset format required by a model                                                                                                                              |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | model_description_url | String                | URL of the model description                                                                                                                                    |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | parameter             | String                | Running parameters of a model. This parameter is a container environment variable when a training job uses a custom image. For details, see the sample request. |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time           | Long                  | Time when a model is created                                                                                                                                    |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | engine_id             | Long                  | Engine ID of a model                                                                                                                                            |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | engine_name           | String                | Engine name of a model                                                                                                                                          |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | engine_version        | String                | Engine version of a model                                                                                                                                       |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 5** **parameter** parameters

   ========= ======= ================================
   Parameter Type    Description
   ========= ======= ================================
   label     String  Parameter name
   value     String  Parameter value
   required  Boolean Whether a parameter is mandatory
   ========= ======= ================================

Samples
-------

The following shows how to query the algorithm whose name contains **configname**.

-  Sample request

   .. code-block::

      GET https://endpoint//v1/{project_id}/built-in-algorithms?per_page=10&page=1&sortBy=engine&order=asc&search_content=model

-  Successful sample response

   .. code-block::

      {
          "models": [
              {
                  "model_id": 4,
                  "model_name": "ResNet_v2_50",
                  "model_usage": 1,
                  "model_precision": "75.55%(top1), 92.6%(top5)",
                  "model_size": 102503801,
                  "model_train_dataset": "ImageNet, 1,000 classes for image classification",
                  "model_dataset_format": "shape: [H>=32, W>=32, C>=1]; type: int8",
                  "model_description_url": "https://github.com/apache/incubator-mxnet/blob/master/example/image-classification/symbols/resnet.py",
                  "parameter": "[{\"label\":\"batch_size\",\"value\":\"4\",\"placeholder_cn\":\"Total number of training images updated each time\",\"placeholder_en\":\"\",\"required\":true},{\"label\":\"lr\",\"value\":\"0.0001\",\"placeholder_cn\":\"Learning rate\",\"placeholder_en\":\"\",\"required\":true},{\"label\":\"save_frequency\",\"value\":\"1\",\"placeholder_cn\":\"Interval for saving the model, indicating that the model is saved every N epochs\",\"placeholder_en\":\"\",\"required\":true},{\"label\":\"num_classes\",\"value\":\"\",\"placeholder_cn\":\"Total number of image classes in training\",\"placeholder_en\":\"\",\"required\":true},{\"label\":\"num_epoch\",\"value\":\"10\",\"placeholder_cn\":\"Number of training epochs\",\"placeholder_en\":\"\",\"required\":true}]",
                  "create_time": 1522218780025,
                  "engine_id": 501,
                  "engine_name": "MXNet",
                  "engine_version": "MXNet-1.2.1-python2.7"
              },
              {
                  "model_id": 5,
                  "model_name": "Faster_RCNN_ResNet_v2_101",
                  "model_usage": 2,
                  "model_precision": "80.05%(mAP)",
                  "model_size": 190936449,
                  "model_train_dataset": "PASCAL VOC2007, 20 classes for object detection",
                  "model_dataset_format": "shape: [H, W, C==3]; type: int8",
                  "model_description_url": "https://github.com/apache/incubator-mxnet/tree/master/example/rcnn",
                  "parameter": "[{\"label\":\"lr\",\"value\":\"0.0001\",\"placeholder_cn\":\"Learning rate\",\"placeholder_en\":\"\",\"required\":true},{\"label\":\"eval_frequence\",\"value\":\"1\",\"placeholder_cn\":\"Frequency for validating the model. By default, validation is performed every epoch.\",\"placeholder_en\":\"\",\"required\":true},{\"label\":\"mom\",\"value\":\"0.9\",\"placeholder_cn\":\"Momentum of the training network\",\"placeholder_en\":\"\",\"required\":true},{\"label\":\"wd\",\"value\":\"0.0005\",\"placeholder_cn\":\"Weight decay coefficient\",\"placeholder_en\":\"\",\"required\":true},{\"label\":\"num_classes\",\"value\":\"\",\"placeholder_cn\":\"Total number of image classes in training. The value must plus 1 because there is a background class.\",\"placeholder_en\":\"\",\"required\":true}]",
                  "create_time": 1525313224596,
                  "engine_id": 501,
                  "engine_name": "MXNet",
                  "engine_version": "MXNet-1.2.1-python2.7"
              }
          ],
          "model_total_count": 41,
          "is_success": true
      }

-  Failed sample response

   .. code-block::

      {
          "is_success": false,
          "error_message": "Error string",
          "error_code": "ModelArts.0105"
      }

Status Code
-----------

For details about the status code, see :ref:`Status Code <modelarts_03_0094>`.
