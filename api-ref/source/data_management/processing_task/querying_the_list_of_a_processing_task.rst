.. _ListProcessorTasks:

Querying the List of a Processing Task
======================================

Function
--------

This API is used to query the list of a processing task. You can query the feature analysis tasks and data processing tasks. You can specify the **task_type** parameter to query the list of a specific type of tasks.

-  Feature analysis refers to the process of analyzing the features of an image based on the image or target box, such as the blurring degree and brightness, and drawing a visualized curve to help process the dataset.

-  Data processing refers to extracting or generating data that is valuable and meaningful to a particular person from a large amount of, cluttered, and incomprehensible data. Data processing includes data validation, data cleansing, data selection, and data augmentation.

-  Data validation indicates that the dataset is verified to ensure data accuracy.

-  Data cleansing refers to the process of denoising, correcting, or supplementing data.

-  Data selection indicates the process of selecting data subsets from full data.

-  Data augmentation indicates that data volume is increased through simple data amplification operations such as scaling, cropping, transformation, and composition.

URI
---

GET /v2/{project_id}/processor-tasks

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                        |
   +============+===========+========+====================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <modelarts_03_0147>`. |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                  |
   +=================+=================+=================+==============================================================================================================================================================================+
   | limit           | No              | Integer         | Maximum number of records returned on each page. The value ranges from 1 to 100. The default value is **10**.                                                                |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset          | No              | Integer         | Start page of the paging list. The default value is **0**.                                                                                                                   |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | order           | No              | String          | Sorting sequence of the query. The options are as follows:                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  **asc**: ascending order                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  **desc**: descending order (default value)                                                                                                                                |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | query_current   | No              | Boolean         | Whether to query only the latest tasks of dataset version. The options are as follows:                                                                                       |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  **true**: Query only the latest tasks of the dataset version.                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  **false**: Query all tasks of the dataset version. (Default value)                                                                                                        |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | return_result   | No              | Boolean         | Whether to return the task result. The options are as follows:                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  **true**: Return the task result. (Default value)                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  **false**: Do not return the task result.                                                                                                                                 |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sort_by         | No              | String          | Sorting mode of the query. The options are as follows:                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  **create_time**: Sort by creation time. (Default value)                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  **name**: Sort by task name.                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  **duration_seconds**: Sort by running time.                                                                                                                               |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | source          | No              | String          | Data source path of the query. The options are as follows:                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  If **type** is set to **OBS**, **source** is an OBS path.                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  If **type** is set to **TASK**, **source** is a task ID.                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  If **type** is set to **DATASET**, **source** is a dataset ID.                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  If **type** is set to **CUSTOM** and the API is called by resource tenants, set **source** to the **project_id** of the actual user. Otherwise, this field is left blank. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | source_type     | No              | String          | Data source type of the query. If this parameter is not specified, all data sources are queried by default. The options are as follows:                                      |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  **OBS**: Data obtained from OBS                                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  **TASK**: Data processing task                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  **DATASET**: Dataset                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  **CUSTOM**: Data called by resource tenants                                                                                                                               |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status          | No              | Integer         | Task status of the query. If this parameter is not specified, tasks in all states are queried by default. The options are as follows:                                        |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  **0**: initialized                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  **1**: running                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  **2**: completed                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  **3**: failed                                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  **4**: stopped                                                                                                                                                            |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | task_name       | No              | String          | Fuzzy search keyword.                                                                                                                                                        |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | task_type       | No              | String          | Task type, that is, ID of a data processing template. The options are as follows:                                                                                            |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  **sys_data_analyse**: feature analysis                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  **sys_data_cleaning**: data cleansing                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  **sys_data_augmentation**: data augmentation                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  **sys_data_validation**: data validation                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                              |
   |                 |                 |                 | -  **sys_data_selection**: data selection                                                                                                                                    |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version_id      | No              | Array           | Version ID list of a specific dataset of the query.                                                                                                                          |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | workspace_id    | No              | String          | Workspace ID. If no workspace is created, the default value is **0**. If a workspace is created and used, use the actual value.                                              |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------+------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | Parameter | Type                                                                                                       | Description                                |
   +===========+============================================================================================================+============================================+
   | count     | Integer                                                                                                    | Total number of data processing tasks.     |
   +-----------+------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | tasks     | Array of :ref:`DescribeProcessorTaskResp <listprocessortasks__response_describeprocessortaskresp>` objects | Data processing task list queried by page. |
   +-----------+------------------------------------------------------------------------------------------------------------+--------------------------------------------+

.. _listprocessortasks__response_describeprocessortaskresp:

.. table:: **Table 4** DescribeProcessorTaskResp

   +-----------------------+------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                           | Description                                                                                                                                               |
   +=======================+================================================================================================+===========================================================================================================================================================+
   | create_time           | Long                                                                                           | Time when a data processing task is created.                                                                                                              |
   +-----------------------+------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | data_source           | :ref:`ProcessorDataSource <listprocessortasks__response_processordatasource>` object           | Input of a data processing task. Either this parameter or **inputs** is delivered.                                                                        |
   +-----------------------+------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                                                                                         | Description of a data processing task.                                                                                                                    |
   +-----------------------+------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | duration_seconds      | Integer                                                                                        | Running time of data processing, in seconds.                                                                                                              |
   +-----------------------+------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | error_msg             | String                                                                                         | Error message. This field is displayed when the value of status is **3**.                                                                                 |
   +-----------------------+------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | inputs                | Array of :ref:`ProcessorDataSource <listprocessortasks__response_processordatasource>` objects | Input channel list of a data processing task. Either this parameter or **data_source** is delivered.                                                      |
   +-----------------------+------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | is_current            | Boolean                                                                                        | Whether the current task is the latest of the same type of this version.                                                                                  |
   +-----------------------+------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                                                                                         | Name of a data processing task.                                                                                                                           |
   +-----------------------+------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | result                | Object                                                                                         | Output result of a data processing task. This field is displayed when status is set to **2** and is valid for a feature analysis task.                    |
   +-----------------------+------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                | Integer                                                                                        | Status of a data processing task. The options are as follows:                                                                                             |
   |                       |                                                                                                |                                                                                                                                                           |
   |                       |                                                                                                | -  **0**: initialized                                                                                                                                     |
   |                       |                                                                                                |                                                                                                                                                           |
   |                       |                                                                                                | -  **1**: running                                                                                                                                         |
   |                       |                                                                                                |                                                                                                                                                           |
   |                       |                                                                                                | -  **2**: completed                                                                                                                                       |
   |                       |                                                                                                |                                                                                                                                                           |
   |                       |                                                                                                | -  **3**: failed                                                                                                                                          |
   |                       |                                                                                                |                                                                                                                                                           |
   |                       |                                                                                                | -  **4**: stopped                                                                                                                                         |
   +-----------------------+------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | task_id               | String                                                                                         | ID of a data processing task.                                                                                                                             |
   +-----------------------+------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | template              | :ref:`TemplateParam <listprocessortasks__response_templateparam>` object                       | Data processing template, such as the algorithm ID and parameters.                                                                                        |
   +-----------------------+------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version_count         | Integer                                                                                        | Version number of a data processing task.                                                                                                                 |
   +-----------------------+------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version_id            | String                                                                                         | Dataset version ID corresponding to a data processing task.                                                                                               |
   +-----------------------+------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version_name          | String                                                                                         | Dataset version name corresponding to a data processing task.                                                                                             |
   +-----------------------+------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | work_path             | :ref:`WorkPath <listprocessortasks__response_workpath>` object                                 | Working directory of a data processing task.                                                                                                              |
   +-----------------------+------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | workspace_id          | String                                                                                         | Workspace ID of a data processing task. If no workspace is created, the default value is **0**. If a workspace is created and used, use the actual value. |
   +-----------------------+------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _listprocessortasks__response_processordatasource:

.. table:: **Table 5** ProcessorDataSource

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                  |
   +=======================+=======================+==============================================================================================================================================================================+
   | name                  | String                | Dataset name.                                                                                                                                                                |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | source                | String                | Data source path. The options are as follows:                                                                                                                                |
   |                       |                       |                                                                                                                                                                              |
   |                       |                       | -  If **type** is set to **OBS**, **source** is an OBS path.                                                                                                                 |
   |                       |                       |                                                                                                                                                                              |
   |                       |                       | -  If **type** is set to **TASK**, **source** is a task ID.                                                                                                                  |
   |                       |                       |                                                                                                                                                                              |
   |                       |                       | -  If **type** is set to **DATASET**, **source** is a dataset ID.                                                                                                            |
   |                       |                       |                                                                                                                                                                              |
   |                       |                       | -  If **type** is set to **CUSTOM** and the API is called by resource tenants, set **source** to the **project_id** of the actual user. Otherwise, this field is left blank. |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type                  | String                | Data source type. The options are as follows:                                                                                                                                |
   |                       |                       |                                                                                                                                                                              |
   |                       |                       | -  **OBS**: Data obtained from OBS                                                                                                                                           |
   |                       |                       |                                                                                                                                                                              |
   |                       |                       | -  **TASK**: Data processing task                                                                                                                                            |
   |                       |                       |                                                                                                                                                                              |
   |                       |                       | -  **DATASET**: Dataset                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                              |
   |                       |                       | -  **CUSTOM**: Data called by resource tenants                                                                                                                               |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version_id            | String                | Version of a dataset.                                                                                                                                                        |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version_name          | String                | Dataset version name.                                                                                                                                                        |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _listprocessortasks__response_templateparam:

.. table:: **Table 6** TemplateParam

   +-----------------------+------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+
   | Parameter             | Type                                                                               | Description                                                                       |
   +=======================+====================================================================================+===================================================================================+
   | id                    | String                                                                             | Task type, that is, ID of a data processing template. The options are as follows: |
   |                       |                                                                                    |                                                                                   |
   |                       |                                                                                    | -  **sys_data_analyse**: feature analysis                                         |
   |                       |                                                                                    |                                                                                   |
   |                       |                                                                                    | -  **sys_data_cleaning**: data cleansing                                          |
   |                       |                                                                                    |                                                                                   |
   |                       |                                                                                    | -  **sys_data_augmentation**: data augmentation                                   |
   |                       |                                                                                    |                                                                                   |
   |                       |                                                                                    | -  **sys_data_validation**: data validation                                       |
   |                       |                                                                                    |                                                                                   |
   |                       |                                                                                    | -  **sys_data_selection**: data selection                                         |
   +-----------------------+------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+
   | name                  | String                                                                             | Template name.                                                                    |
   +-----------------------+------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+
   | operator_params       | Array of :ref:`OperatorParam <listprocessortasks__response_operatorparam>` objects | Operator parameter list.                                                          |
   +-----------------------+------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+

.. _listprocessortasks__response_operatorparam:

.. table:: **Table 7** OperatorParam

   +------------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter              | Type    | Description                                                                                                                                                                                                                                                                                                                                                  |
   +========================+=========+==============================================================================================================================================================================================================================================================================================================================================================+
   | advanced_params_switch | Boolean | Advanced parameter switch.                                                                                                                                                                                                                                                                                                                                   |
   +------------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                     | String  | ID of an operator.                                                                                                                                                                                                                                                                                                                                           |
   +------------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                   | String  | Name of an operator.                                                                                                                                                                                                                                                                                                                                         |
   +------------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | params                 | Object  | Operator parameter. The parameter type is map<string,object>. Currently, object only supports the types of Boolean, Integer, Long, String, List and Map<String,String>. For two special scenarios of object detection and image classification in a data preprocessing task, the value of **task_type** is **object_detection** or **image_classification**. |
   +------------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _listprocessortasks__response_workpath:

.. table:: **Table 8** WorkPath

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                              |
   +=======================+=======================+==========================================================================================================================================+
   | name                  | String                | Dataset name.                                                                                                                            |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | output_path           | String                | Output path.                                                                                                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | path                  | String                | Working path. The options are as follows:                                                                                                |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  If **type** is set to **OBS**, **source** is an OBS path.                                                                             |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  If **type** is set to **DATASET**, **source** is a dataset ID.                                                                        |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | type                  | String                | Type of a working path. The options are as follows:                                                                                      |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  **OBS**: OBS path                                                                                                                     |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  **DATASET**: dataset                                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | version_id            | String                | Version of a dataset.                                                                                                                    |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | version_name          | String                | Name of a dataset version. The value can contain 0 to 32 characters. Only digits, letters, underscores (_), and hyphens (-) are allowed. |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

Query historical data validation tasks of a specified dataset.

.. code-block::

   GET https://{endpoint}/v2/{project_id}/processor-tasks?offset=0&limit=10&sort_by=create_time&order=desc&source_type=DATASET&source=qjHAs14pRu4n2so1Qlb&task_type=sys_data_validation&return_result=false

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "task_id" : "SSzH9AdmHTvIBeihArb",
     "name" : "PRE-6c83",
     "description" : "test",
     "inputs" : [ {
       "type" : "DATASET",
       "source" : "qjHAs14pRu4n2so1Qlb",
       "version_id" : "cUELhTAYGIR36YpTE5Y",
       "name" : "dataset-dba1",
       "version_name" : "V001"
     } ],
     "work_path" : {
       "type" : "DATASET",
       "path" : "qjHAs14pRu4n2so1Qlb",
       "name" : "dataset-dba1",
       "version_name" : "V002",
       "output_path" : "/test-lxm/data-out/EnyHCFzjTFY20U3sYSE/"
     },
     "template" : {
       "id" : "sys_data_validation",
       "name" : "data validation template name",
       "operator_params" : [ {
         "name" : "MetaValidation",
         "advanced_params_switch" : false,
         "params" : {
           "task_type" : "image_classification",
           "dataset_type" : "manifest",
           "source_service" : "select",
           "filter_func" : "data_validation_select",
           "image_max_width" : "-1",
           "image_max_height" : "-1",
           "total_status" : "[0,1,2]"
         }
       } ]
     },
     "status" : 2,
     "duration_seconds" : 277,
     "create_time" : 1614245065569,
     "workspace_id" : "0",
     "version_count" : 1,
     "ai_project" : ""
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
