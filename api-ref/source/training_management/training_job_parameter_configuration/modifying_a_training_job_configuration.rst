.. _modelarts_03_0060:

Modifying a Training Job Configuration
======================================

Function
--------

This API is used to modify a training job configuration.

URI
---

PUT /v1/{project_id}/training-job-configs/{config_name}

:ref:`Table 1 <modelarts_03_0060__en-us_topic_0131292964_table5935107791848>` describes the required parameters.

.. _modelarts_03_0060__en-us_topic_0131292964_table5935107791848:

.. table:: **Table 1** Parameters

   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                                 |
   +=============+===========+========+=============================================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | config_name | Yes       | String | Name of a training job configuration                                                                                        |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+

Request Body
------------

:ref:`Table 2 <modelarts_03_0060__en-us_topic_0131292964_table5503766015447>` describes the request parameters.

.. _modelarts_03_0060__en-us_topic_0131292964_table5503766015447:

.. table:: **Table 2** Parameters

   +--------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter          | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                    |
   +====================+=================+=================+================================================================================================================================================================================================================================================================================+
   | config_desc        | No              | String          | Description of a training job configuration. The value is a string of 0 to 256 characters. By default, this parameter is left blank.                                                                                                                                           |
   +--------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | worker_server_num  | Yes             | Integer         | Number of workers in a training job. Obtain the maximum value from :ref:`Querying Job Resource Specifications <modelarts_03_0072>`.                                                                                                                                            |
   +--------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | app_url            | Yes             | String          | Code directory of a training job, for example, **/usr/app/**. This parameter must be used together with **boot_file_url**. After setting **model_id**, you do not need to set **app_url** or **boot_file_url**, and **engine_id**.                                             |
   +--------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | boot_file_url      | Yes             | String          | Boot file of a training job, which needs to be stored in the code directory, for example, **/usr/app/boot.py**. This parameter must be used together with **app_url**. After setting **model_id**, you do not need to set **app_url** or **boot_file_url**, and **engine_id**. |
   +--------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | model_id           | Yes             | Long            | Model ID of a training job. After setting **model_id**, you do not need to set **app_url** or **boot_file_url**, and **engine_id**.                                                                                                                                            |
   +--------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | parameter          | No              | Array<Object>   | Running parameters of a training job. It is a collection of label-value pairs. This parameter is a container environment variable when a training job uses a custom image.                                                                                                     |
   +--------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | spec_id            | Yes             | Long            | ID of the resource specifications selected for a training job. Obtain the ID by calling the API described in :ref:`Querying Job Resource Specifications <modelarts_03_0072>`.                                                                                                  |
   +--------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | data_url           | Yes             | String          | OBS URL of the dataset required by a training job, for example, **/usr/data/**.                                                                                                                                                                                                |
   |                    |                 |                 |                                                                                                                                                                                                                                                                                |
   |                    |                 |                 | This parameter cannot be used together with **data_source** or **dataset_id** and **dataset_version_id**. However, one of the parameters must exist.                                                                                                                           |
   +--------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dataset_id         | Yes             | String          | Dataset ID of a training job. This parameter must be used together with **dataset_version_id**, but cannot be used together with **data_url** or **data_source**.                                                                                                              |
   +--------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dataset_version_id | Yes             | String          | Dataset version ID of a training job. This parameter must be used together with **dataset_id**, but cannot be used together with **data_url** or **data_source**.                                                                                                              |
   +--------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | data_source        | Yes             | JSON Array      | Dataset of a training job. This parameter cannot be used together with **data_url** or **dataset_id** and **dataset_version_id**.                                                                                                                                              |
   +--------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | engine_id          | Yes             | Long            | ID of the engine selected for a training job. The default value is **1**. Obtain the ID by calling the API described in :ref:`Querying Job Engine Specifications <modelarts_03_0073>`.                                                                                         |
   +--------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | train_url          | No              | String          | OBS URL of the output file of a training job. By default, this parameter is left blank. Example value: **/usr/train/**                                                                                                                                                         |
   +--------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_url            | No              | String          | OBS URL of the logs of a training job. By default, this parameter is left blank. Example value: **/usr/train/**                                                                                                                                                                |
   +--------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | user_image_url     | No              | String          | SWR URL of a custom image used by a training job. Example value: **100.125.5.235:20202/jobmng/custom-cpu-base:1.0**                                                                                                                                                            |
   +--------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | user_command       | No              | String          | Boot command used to start the container of a custom image of a training job. The format is **bash /home/work/run_train.sh python /home/work/user-job-dir/app/train.py {python_file_parameter}**.                                                                              |
   +--------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** **data_source** parameters

   +-----------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory | Type   | Description                                                                                                                                    |
   +=================+===========+========+================================================================================================================================================+
   | dataset_id      | No        | String | Dataset ID of a training job. This parameter must be used together with **dataset_version_id**, but cannot be used together with **data_url**. |
   +-----------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | dataset_version | No        | String | Dataset version ID of a training job. This parameter must be used together with **dataset_id**, but cannot be used together with **data_url**. |
   +-----------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | type            | No        | String | Dataset type. The value can be **obs** or **dataset**. obs and dataset cannot be used at the same time.                                        |
   +-----------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | data_url        | No        | String | OBS bucket path. This parameter cannot be used together with **dataset_id** or **dataset_version**.                                            |
   +-----------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 4** **parameter** parameters

   ========= ========= ====== ================
   Parameter Mandatory Type   Description
   ========= ========= ====== ================
   label     No        String Parameter name.
   value     No        String Parameter value.
   ========= ========= ====== ================

Response Body
-------------

:ref:`Table 5 <modelarts_03_0060__en-us_topic_0131292964_table5371703815645>` describes the response parameters.

.. _modelarts_03_0060__en-us_topic_0131292964_table5371703815645:

.. table:: **Table 5** Parameters

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

Samples
-------

#. The following shows how to modify the job parameter configuration named **config**.

   -  Sample request

      .. code-block::

         PUT    https://endpoint/v1/{project_id}/training-job-configs/config

         {
             "config_desc": "This is config",
             "worker_server_num": 1,
             "app_url": "/usr/app/",
             "boot_file_url": "/usr/app/boot.py",
             "parameter": [
                 {
                     "label": "learning_rate",
                     "value": 0.01
                 },
                 {
                     "key": "batch_size",
                     "value": 32
                 }
             ],
             "spec_id": 1,
             "dataset_id": "38277e62-9e59-48f4-8d89-c8cf41622c24",
             "dataset_version_id": "2ff0d6ba-c480-45ae-be41-09a8369bfc90",
             "engine_id": 1,
             "train_url": "/usr/train/",
             "log_url": "/usr/log/"
         }

   -  Successful sample response

      .. code-block::

         {
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

For details about the status code, see :ref:`Table 1 <modelarts_03_0094__en-us_topic_0132773864_table1450010510213>`.
