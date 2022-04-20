.. _CreateProcessorTask:

Creating a Processing Task
==========================

Function
--------

This API is used to create a processing task. You can create feature analysis tasks and data processing tasks. You can specify the **id** field of **template** composite parameter in the request body to create a task.

-  Feature analysis refers to the process of analyzing the features of an image based on the image or target box, such as the blurring degree and brightness, and drawing a visualized curve to help process the dataset.

-  Data processing refers to extracting or generating data that is valuable and meaningful to a particular person from a large amount of, cluttered, and incomprehensible data. Data processing includes data validation, data cleansing, data selection, and data augmentation.

-  Data validation indicates that the dataset is verified to ensure data accuracy.

-  Data cleansing refers to the process of denoising, correcting, or supplementing data.

-  Data selection indicates the process of selecting data subsets from full data.

-  Data augmentation indicates that data volume is increased through simple data amplification operations such as scaling, cropping, transformation, and composition.

URI
---

POST /v2/{project_id}/processor-tasks

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                        |
   +============+===========+========+====================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <modelarts_03_0147>`. |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request body parameters

   +-----------------+-----------------+------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                                           | Description                                                                                                                                                                                                                                            |
   +=================+=================+================================================================================================+========================================================================================================================================================================================================================================================+
   | create_version  | No              | Boolean                                                                                        | Whether to synchronously create a task version when creating a task. Set this parameter to **true** only when creating a data processing task. For other types of tasks, this parameter is set to **false** or left blank. The options are as follows: |
   |                 |                 |                                                                                                |                                                                                                                                                                                                                                                        |
   |                 |                 |                                                                                                | -  **true**: Create a task version when creating a task.                                                                                                                                                                                               |
   |                 |                 |                                                                                                |                                                                                                                                                                                                                                                        |
   |                 |                 |                                                                                                | -  **false**: Do not create a task version when creating a task. (Default value)                                                                                                                                                                       |
   +-----------------+-----------------+------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | data_source     | No              | :ref:`ProcessorDataSource <createprocessortask__request_processordatasource>` object           | Data source. Either this parameter or **inputs** is used. A data source path cannot be an OBS path in a KMS-encrypted bucket.                                                                                                                          |
   +-----------------+-----------------+------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description     | No              | String                                                                                         | Description of a data processing task. The description contains 0 to 256 characters and does not support the following special characters: ^!<>=&"'                                                                                                    |
   +-----------------+-----------------+------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | inputs          | No              | Array of :ref:`ProcessorDataSource <createprocessortask__request_processordatasource>` objects | Data sources. Either this parameter or **data_source** is used. A data source path cannot be an OBS path in a KMS-encrypted bucket.                                                                                                                    |
   +-----------------+-----------------+------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name            | Yes             | String                                                                                         | Name of a data processing task.                                                                                                                                                                                                                        |
   +-----------------+-----------------+------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | template        | No              | :ref:`TemplateParam <createprocessortask__request_templateparam>` object                       | Data processing template, such as the algorithm ID and parameters.                                                                                                                                                                                     |
   +-----------------+-----------------+------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version_id      | No              | String                                                                                         | Dataset version ID.                                                                                                                                                                                                                                    |
   +-----------------+-----------------+------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | work_path       | No              | :ref:`WorkPath <createprocessortask__request_workpath>` object                                 | Work directory of a data processing task. A work directory cannot be an OBS path in a KMS-encrypted bucket.                                                                                                                                            |
   +-----------------+-----------------+------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | workspace_id    | No              | String                                                                                         | Workspace ID. If no workspace is created, the default value is **0**. If a workspace is created and used, use the actual value.                                                                                                                        |
   +-----------------+-----------------+------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _createprocessortask__request_processordatasource:

.. table:: **Table 3** ProcessorDataSource

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                  |
   +=================+=================+=================+==============================================================================================================================================================================+
   | name            | No              | String          | Dataset name.                                                                                                                                                                |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | source          | No              | String          | Data source path. The options are as follows:                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  If **type** is set to **OBS**, **source** is an OBS path.                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  If **type** is set to **TASK**, **source** is a task ID.                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  If **type** is set to **DATASET**, **source** is a dataset ID.                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  If **type** is set to **CUSTOM** and the API is called by resource tenants, set **source** to the **project_id** of the actual user. Otherwise, this field is left blank. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type            | No              | String          | Data source type. The options are as follows:                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  **OBS**: Data obtained from OBS                                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  **TASK**: Data processing task                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  **DATASET**: Dataset                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  **CUSTOM**: Data called by resource tenants                                                                                                                               |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version_id      | No              | String          | Version of a dataset.                                                                                                                                                        |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version_name    | No              | String          | Dataset version name.                                                                                                                                                        |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _createprocessortask__request_templateparam:

.. table:: **Table 4** TemplateParam

   +-----------------+-----------------+------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                               | Description                                                                       |
   +=================+=================+====================================================================================+===================================================================================+
   | id              | No              | String                                                                             | Task type, that is, ID of a data processing template. The options are as follows: |
   |                 |                 |                                                                                    |                                                                                   |
   |                 |                 |                                                                                    | -  **sys_data_analyse**: feature analysis                                         |
   |                 |                 |                                                                                    |                                                                                   |
   |                 |                 |                                                                                    | -  **sys_data_cleaning**: data cleansing                                          |
   |                 |                 |                                                                                    |                                                                                   |
   |                 |                 |                                                                                    | -  **sys_data_augmentation**: data augmentation                                   |
   |                 |                 |                                                                                    |                                                                                   |
   |                 |                 |                                                                                    | -  **sys_data_validation**: data validation                                       |
   |                 |                 |                                                                                    |                                                                                   |
   |                 |                 |                                                                                    | -  **sys_data_selection**: data selection                                         |
   +-----------------+-----------------+------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+
   | name            | No              | String                                                                             | Template name.                                                                    |
   +-----------------+-----------------+------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+
   | operator_params | No              | Array of :ref:`OperatorParam <createprocessortask__request_operatorparam>` objects | Operator parameter list.                                                          |
   +-----------------+-----------------+------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+

.. _createprocessortask__request_operatorparam:

.. table:: **Table 5** OperatorParam

   +------------------------+-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter              | Mandatory | Type    | Description                                                                                                                                                                                                                                                                                                                                                  |
   +========================+===========+=========+==============================================================================================================================================================================================================================================================================================================================================================+
   | advanced_params_switch | No        | Boolean | Advanced parameter switch.                                                                                                                                                                                                                                                                                                                                   |
   +------------------------+-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                     | No        | String  | ID of an operator.                                                                                                                                                                                                                                                                                                                                           |
   +------------------------+-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                   | No        | String  | Name of an operator.                                                                                                                                                                                                                                                                                                                                         |
   +------------------------+-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | params                 | No        | Object  | Operator parameter. The parameter type is map<string,object>. Currently, object only supports the types of Boolean, Integer, Long, String, List and Map<String,String>. For two special scenarios of object detection and image classification in a data preprocessing task, the value of **task_type** is **object_detection** or **image_classification**. |
   +------------------------+-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _createprocessortask__request_workpath:

.. table:: **Table 6** WorkPath

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                              |
   +=================+=================+=================+==========================================================================================================================================+
   | name            | No              | String          | Dataset name.                                                                                                                            |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | output_path     | No              | String          | Output path.                                                                                                                             |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | path            | No              | String          | Working path. The options are as follows:                                                                                                |
   |                 |                 |                 |                                                                                                                                          |
   |                 |                 |                 | -  If **type** is set to **OBS**, **source** is an OBS path.                                                                             |
   |                 |                 |                 |                                                                                                                                          |
   |                 |                 |                 | -  If **type** is set to **DATASET**, **source** is a dataset ID.                                                                        |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | type            | No              | String          | Type of a working path. The options are as follows:                                                                                      |
   |                 |                 |                 |                                                                                                                                          |
   |                 |                 |                 | -  **OBS**: OBS path                                                                                                                     |
   |                 |                 |                 |                                                                                                                                          |
   |                 |                 |                 | -  **DATASET**: dataset                                                                                                                  |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | version_id      | No              | String          | Version of a dataset.                                                                                                                    |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | version_name    | No              | String          | Name of a dataset version. The value can contain 0 to 32 characters. Only digits, letters, underscores (_), and hyphens (-) are allowed. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 7** Response body parameters

   ========= ====== =============================
   Parameter Type   Description
   ========= ====== =============================
   task_id   String ID of a data processing task.
   ========= ====== =============================

Example Requests
----------------

-  Creating a Data Processing (Data Validation) Task

   .. code-block::

      {
        "name" : "PRE-e77c",
        "inputs" : [ {
          "type" : "DATASET",
          "source" : "PYc9H2HGv5BJNwBGXyK",
          "version_id" : "yoJ5ssClpNlOrsjjFDa"
        } ],
        "work_path" : {
          "type" : "DATASET",
          "path" : "PYc9H2HGv5BJNwBGXyK",
          "version_name" : "V0010"
        },
        "description" : "",
        "create_version" : true,
        "template" : {
          "id" : "sys_data_validation",
          "operator_params" : [ {
            "name" : "MetaValidation",
            "advanced_params_switch" : false,
            "params" : {
              "task_type" : "image_classification",
              "dataset_type" : "manifest",
              "source_service" : "select",
              "filter_func" : "data_validation_select",
              "image_max_width" : "1920",
              "image_max_height" : "1920",
              "total_status" : "[0,1,2]"
            }
          } ]
        },
        "workspace_id" : "0"
      }

-  Creating a Data Processing (Data Cleansing) Task

   .. code-block::

      {
        "name" : "PRE-330f",
        "inputs" : [ {
          "type" : "DATASET",
          "source" : "gfghHSokody6AJigS5A",
          "version_id" : "54IXbeJhfttGpL46lbv"
        } ],
        "work_path" : {
          "type" : "DATASET",
          "path" : "gfghHSokody6AJigS5A",
          "version_name" : "V004"
        },
        "description" : "",
        "create_version" : true,
        "template" : {
          "id" : "sys_data_cleaning",
          "operator_params" : [ {
            "name" : "PCC",
            "advanced_params_switch" : false,
            "params" : {
              "task_type" : "image_classification",
              "dataset_type" : "manifest",
              "source_service" : "select",
              "filter_func" : "data_cleaning_select",
              "prototype_sample_path" : "obs://test-obs/classify/data/cat-dog/",
              "criticism_sample_path" : "",
              "n_clusters" : "auto",
              "simlarity_threshold" : "0.9",
              "embedding_distance" : "0.2",
              "checkpoint_path" : "/home/work/user-job-dir/test-lxm/resnet_v1_50",
              "total_status" : "[0,2]",
              "do_validation" : "True"
            }
          } ]
        },
        "workspace_id" : "0"
      }

-  Creating a Data Processing (Data Selection) Task

   .. code-block::

      {
        "name" : "PRE-aae5",
        "inputs" : [ {
          "type" : "DATASET",
          "source" : "gLNSdlQ1iAAmPgl0Won",
          "version_id" : "WAVPSYpKE3FggbgRxiK"
        } ],
        "work_path" : {
          "type" : "DATASET",
          "path" : "gLNSdlQ1iAAmPgl0Won",
          "version_name" : "V003"
        },
        "description" : "",
        "create_version" : true,
        "template" : {
          "id" : "sys_data_selection",
          "operator_params" : [ {
            "name" : "SimDeduplication",
            "advanced_params_switch" : false,
            "params" : {
              "task_type" : "image_classification",
              "dataset_type" : "manifest",
              "source_service" : "select",
              "filter_func" : "data_deduplication_select",
              "simlarity_threshold" : "0.9",
              "total_status" : "[0,2]",
              "do_validation" : "True"
            }
          } ]
        },
        "workspace_id" : "0"
      }

-  Creating a Data Processing (Data Augmentation) Task

   .. code-block::

      {
        "name" : "PRE-637c",
        "inputs" : [ {
          "type" : "DATASET",
          "source" : "XGrRZuCV1qmMxnsmD5u",
          "version_id" : "kjPDTOSi6BQqhtXZlFv"
        } ],
        "work_path" : {
          "type" : "DATASET",
          "path" : "XGrRZuCV1qmMxnsmD5u",
          "version_name" : "V002"
        },
        "description" : "",
        "create_version" : true,
        "template" : {
          "id" : "sys_data_augmentation",
          "operator_params" : [ {
            "name" : "AddNoise",
            "advanced_params_switch" : false,
            "params" : {
              "task_type" : "image_classification",
              "dataset_type" : "manifest",
              "AddNoise" : "1",
              "noise_type" : "Gauss",
              "loc" : "0",
              "scale" : "1",
              "lam" : "2",
              "p" : "0.01",
              "total_status" : "[3]",
              "filter_func" : "data_augmentation",
              "do_validation" : "True"
            }
          } ]
        },
        "workspace_id" : "0"
      }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "task_id" : "SNEJua7qdZZN8GvkcEr"
   }

Status Codes
------------

=========== ============
Status Code Description
=========== ============
200         OK
401         Unauthorized
403         Forbidden
404         Not Found
=========== ============

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
