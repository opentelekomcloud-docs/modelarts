:original_name: modelarts_03_0045.html

.. _modelarts_03_0045:

Creating a Training Job
=======================

Function
--------

This API is used to create a training job.

Calling this API is an asynchronous operation. The job status can be obtained by calling the APIs described in :ref:`Querying a Training Job List <modelarts_03_0046>` and :ref:`Querying the Details About a Training Job Version <modelarts_03_0047>`.

URI
---

POST /v1/{project_id}/training-jobs

:ref:`Table 1 <en-us_topic_0000001943866685__table143351836151117>` describes the required parameters.

.. _en-us_topic_0000001943866685__table143351836151117:

.. table:: **Table 1** Parameters

   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                               |
   +============+===========+========+===========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+

Request Body
------------

:ref:`Table 2 <en-us_topic_0000001943866685__table6270801111211>` describes the request parameters.

.. _en-us_topic_0000001943866685__table6270801111211:

.. table:: **Table 2** Parameters

   +--------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                        |
   +==============+===========+========+====================================================================================================================================+
   | job_name     | Yes       | String | Training job name. The value must contain 1 to 64 characters consisting of only digits, letters, underscores (_), and hyphens (-). |
   +--------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------+
   | job_desc     | No        | String | Description of a training job. The value must contain 0 to 256 characters. By default, this parameter is left blank.               |
   +--------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------+
   | config       | Yes       | Object | Parameters for creating a training job For details, see :ref:`Table 3 <en-us_topic_0000001943866685__table24411850104213>`.        |
   +--------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------+
   | workspace_id | No        | String | Workspace where a job resides. Default value: **0**                                                                                |
   +--------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000001943866685__table24411850104213:

.. table:: **Table 3** **config** parameters

   +--------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter          | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                                                                                                                       |
   +====================+=================+=================+===================================================================================================================================================================================================================================================================================================================================================================================================+
   | worker_server_num  | Yes             | Integer         | Number of workers in a training job. Obtain the maximum value from the **max_num** value returned by the API in :ref:`Querying Job Resource Specifications <modelarts_03_0072>`.                                                                                                                                                                                                                  |
   +--------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | app_url            | Yes             | String          | Code directory of a training job, for example, **/usr/app/**. This parameter must be used together with **boot_file_url**. After setting **model_id**, you do not need to set **app_url** or **boot_file_url**, and **engine_id**.                                                                                                                                                                |
   +--------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | boot_file_url      | Yes             | String          | Boot file of a training job, which needs to be stored in the code directory. Example value: **/usr/app/boot.py** This parameter must be used together with **app_url**. After setting **model_id**, you do not need to set **app_url** or **boot_file_url**, and **engine_id**.                                                                                                                   |
   +--------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | parameter          | No              | Array<Object>   | Running parameters of a training job. It is a collection of label-value pairs. Values can be customized. **label** is a parameter name and **value** is the parameter value. For details, see the sample request. This parameter is a container environment variable when a training job uses a custom image. For details, see :ref:`Table 8 <en-us_topic_0000001943866685__table1267642234716>`. |
   +--------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | data_url           | No              | String          | OBS URL of the dataset required by a training job. By default, this parameter is left blank. For example, **/usr/data/**. This parameter cannot be used together with **data_source** or **dataset_id** and **dataset_version_id**. However, one of the parameters must exist.                                                                                                                    |
   +--------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dataset_id         | No              | String          | Dataset ID of a training job. This parameter must be used together with **dataset_version_id**, but cannot be used together with **data_url** or **data_source**.                                                                                                                                                                                                                                 |
   +--------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dataset_version_id | No              | String          | Dataset version ID of a training job. This parameter must be used together with **dataset_id**, but cannot be used together with **data_url** or **data_source**.                                                                                                                                                                                                                                 |
   +--------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | data_source        | No              | Array<Object>   | Dataset of a training job. This parameter cannot be used together with **data_url** or **dataset_id** and **dataset_version_id**. For details, see :ref:`Table 4 <en-us_topic_0000001943866685__table250595919011>`.                                                                                                                                                                              |
   +--------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | spec_id            | Yes             | Long            | ID of the resource specifications selected for a training job. Obtain the ID by calling the API described in :ref:`Querying Job Resource Specifications <modelarts_03_0072>`. When creating a public pool job, ensure that **spec_id** is mandatory and cannot be used with **pool_id**.                                                                                                          |
   +--------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | pool_id            | Yes             | String          | ID of a dedicated resource pool. To obtain the ID, do as follows: Log in to the ModelArts management console, choose **Dedicated Resource Pools** in the navigation pane on the left, and view the resource pool ID in the dedicated resource pool list. When creating a dedicated pool job, ensure that **pool_id** is mandatory and cannot be used with **spec_id**.                            |
   +--------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | engine_id          | Yes             | Long            | ID of the engine selected for a training job. The default value is **1**. After setting **model_id**, you do not need to set **app_url** or **boot_file_url**, and **engine_id**. Obtain the ID by calling the API described in :ref:`Querying Job Engine Specifications <modelarts_03_0073>`.                                                                                                    |
   +--------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | train_url          | No              | String          | OBS URL of the output file of a training job. By default, this parameter is left blank. Example value: **/usr/train/**                                                                                                                                                                                                                                                                            |
   +--------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_url            | No              | String          | OBS URL of the logs of a training job. By default, this parameter is left blank. Example value: **/usr/log/**                                                                                                                                                                                                                                                                                     |
   +--------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | user_image_url     | No              | String          | SWR URL of a custom image used by a training job. Example value: **100.125.5.235:20202/jobmng/custom-cpu-base:1.0**                                                                                                                                                                                                                                                                               |
   +--------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | user_command       | No              | String          | Boot command used to start the container of a custom image of a training job. The format is **bash /home/work/run_train.sh python /home/work/user-job-dir/app/train.py {python_file_parameter}**.                                                                                                                                                                                                 |
   +--------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_version     | No              | Boolean         | Whether a version is created when a training job is created                                                                                                                                                                                                                                                                                                                                       |
   |                    |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                                   |
   |                    |                 |                 | -  **true**: Default value. A version is created when a training job is created.                                                                                                                                                                                                                                                                                                                  |
   |                    |                 |                 | -  **false**: A version is not created when a training job is created.                                                                                                                                                                                                                                                                                                                            |
   +--------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | volumes            | No              | JSON Array      | Storage volume that can be used by a training job. For details, see :ref:`Table 5 <en-us_topic_0000001943866685__table6403153714711>`.                                                                                                                                                                                                                                                            |
   +--------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000001943866685__table250595919011:

.. table:: **Table 4** **data_source** parameters

   +-----------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory | Type   | Description                                                                                                                                    |
   +=================+===========+========+================================================================================================================================================+
   | dataset_id      | No        | String | Dataset ID of a training job. This parameter must be used together with **dataset_version_id**, but cannot be used together with **data_url**. |
   +-----------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | dataset_version | No        | String | Dataset version ID of a training job. This parameter must be used together with **dataset_id**, but cannot be used together with **data_url**. |
   +-----------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | type            | No        | String | Dataset type. The value can be **obs** or **dataset**. **obs** and **dataset** cannot be used at the same time.                                |
   +-----------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | data_url        | No        | String | OBS bucket path. This parameter cannot be used together with **dataset_id** or **dataset_version**.                                            |
   +-----------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000001943866685__table6403153714711:

.. table:: **Table 5** **volumes** parameters

   +-----------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                                                                                                                                                       |
   +===========+===========+========+===================================================================================================================================================================================================================================================================+
   | nfs       | No        | Object | Storage volume of the shared file system type. Only the training jobs running in a resource pool with the shared file system network connected support such storage volumes. For details, see :ref:`Table 6 <en-us_topic_0000001943866685__table19871043113315>`. |
   +-----------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | host_path | No        | Object | Storage volume of the host file system type. Only training jobs running in a dedicated resource pool support such storage volumes. For details, see :ref:`Table 7 <en-us_topic_0000001943866685__table4873028185611>`.                                            |
   +-----------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000001943866685__table19871043113315:

.. table:: **Table 6** **nfs** parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                         |
   +=================+=================+=================+=====================================================================+
   | id              | Yes             | String          | ID of an SFS Turbo file system                                      |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------+
   | src_path        | Yes             | String          | Address of an SFS Turbo file system                                 |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------+
   | dest_path       | Yes             | String          | Local path to a training job                                        |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------+
   | read_only       | No              | Boolean         | Whether **dest_path** is read-only. The default value is **false**. |
   |                 |                 |                 |                                                                     |
   |                 |                 |                 | -  **true**: read-only permission                                   |
   |                 |                 |                 | -  **false**: read/write permission. This is the default value.     |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------+

.. _en-us_topic_0000001943866685__table4873028185611:

.. table:: **Table 7** **host_path** parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                         |
   +=================+=================+=================+=====================================================================+
   | src_path        | Yes             | String          | Local path to a host                                                |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------+
   | dest_path       | Yes             | String          | Local path to a training job                                        |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------+
   | read_only       | No              | Boolean         | Whether **dest_path** is read-only. The default value is **false**. |
   |                 |                 |                 |                                                                     |
   |                 |                 |                 | -  **true**: read-only permission                                   |
   |                 |                 |                 | -  **false**: read/write permission. This is the default value.     |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------+

.. _en-us_topic_0000001943866685__table1267642234716:

.. table:: **Table 8** **parameter** parameters

   ========= ========= ====== ===============
   Parameter Mandatory Type   Description
   ========= ========= ====== ===============
   label     No        String Parameter name
   value     No        String Parameter value
   ========= ========= ====== ===============

Response Body
-------------

:ref:`Table 9 <en-us_topic_0000001943866685__table1260716526159>` describes the response parameters.

.. _en-us_topic_0000001943866685__table1260716526159:

.. table:: **Table 9** Parameters

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                |
   +=======================+=======================+============================================================================================================+
   | is_success            | Boolean               | Whether the request is successful                                                                          |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | error_message         | String                | Error message of a failed API call.                                                                        |
   |                       |                       |                                                                                                            |
   |                       |                       | This parameter is not included when the API call succeeds.                                                 |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | error_code            | String                | Error code of a failed API call. For details, see :ref:`Error Codes <modelarts_03_0095>`.                  |
   |                       |                       |                                                                                                            |
   |                       |                       | This parameter is not included when the API call succeeds.                                                 |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | job_id                | Long                  | ID of a training job                                                                                       |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | job_name              | String                | Name of a training job                                                                                     |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | status                | Int                   | Status of a training job. For details about the job statuses, see :ref:`Job Statuses <modelarts_03_0074>`. |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | create_time           | Long                  | Timestamp when a training job is created                                                                   |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | version_id            | Long                  | Version ID of a training job                                                                               |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | resource_id           | String                | Charged resource ID of a training job                                                                      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | version_name          | String                | Version name of a training job                                                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------+

Sample Request
--------------

-  The following shows how to create training job **TestModelArtsJob** with **This is a ModelArts job** as its description.

   .. code-block:: text

      POST    https://endpoint/v1/{project_id}/training-jobs
      {
          "job_name": "TestModelArtsJob",
          "job_desc": "This is a ModelArts job",
          "workspace_id": "af261af2218841ec960b01ab3cf1a5fa",
          "config": {
              "worker_server_num": 1,
              "app_url": "/usr/app/",
              "boot_file_url": "/usr/app/boot.py",
              "parameter": [
                  {
                      "label": "learning_rate",
                      "value": "0.01"
                  },
                  {
                      "label": "batch_size",
                      "value": "32"
                  }
              ],
              "dataset_id": "38277e62-9e59-48f4-8d89-c8cf41622c24",
              "dataset_version_id": "2ff0d6ba-c480-45ae-be41-09a8369bfc90",
              "spec_id": 1,
              "engine_id": 1,
              "train_url": "/usr/train/",
              "log_url": "/usr/log/",
              "model_id": 1,
              "pool_id": "testpool"
          }
      }

-  The following shows how to create training job **TestModelArtsJob2** using a custom image.

   .. code-block:: text

      POST    https://endpoint/v1/{project_id}/training-jobs
      {
          "job_name": "TestModelArtsJob2",
          "job_desc": "This is a ModelArts job",
          "workspace_id": "af261af2218841ec960b01ab3cf1a5fa",
          "config": {
              "worker_server_num": 1,
              "data_url": "/usr/data/",
              "app_url": "/usr/app/",
              "boot_file_url": "/usr/app/boot.py",
              "parameter": [
                  {
                      "label": "CUSTOM_PARAM1",
                      "value": "1"
                  }
              ],
              "spec_id": 1,
              "user_command": "bash -x /home/work/run_train.sh python /home/work/user-job-dir/app/mnist/mnist_softmax.py --data_url /home/work/user-job-dir/app/mnist_data",
              "user_image_url": "100.125.5.235:20202/jobmng/custom-cpu-base:1.0",
              "train_url": "/usr/train/",
              "log_url": "/usr/log/",
              "model_id": 1,
              "pool_id": "testpool",
              "engine_id": 1
          }
      }

-  The following shows how to create training job **TestModelArtsJob3** using disk storage.

   .. code-block:: text

      POST    https://endpoint/v1/{project_id}/training-jobs
      {
          "job_name": "TestModelArtsJob3",
          "job_desc": "This is a ModelArts job",
          "workspace_id": "af261af2218841ec960b01ab3cf1a5fa",
          "config": {
              "worker_server_num": 1,
              "app_url": "/usr/app/",
              "boot_file_url": "/usr/app/boot.py",
              "parameter": [
                  {
                      "label": "learning_rate",
                      "value": "0.01"
                  },
                  {
                      "label": "batch_size",
                      "value": "32"
                  }
              ],
              "dataset_id": "38277e62-9e59-48f4-8d89-c8cf41622c24",
              "dataset_version_id": "2ff0d6ba-c480-45ae-be41-09a8369bfc90",
              "spec_id": 1,
              "engine_id": 1,
              "train_url": "/usr/train/",
              "log_url": "/usr/log/",
              "model_id": 1,
              "pool_id": "testpool",
              "volumes": [
                  {
                      "nfs": {
                          "id": "43b37236-9afa-4855-8174-32254b9562e7",
                          "src_path": "192.168.8.150:/",
                          "dest_path": "/home/work/nas",
                          "read_only": false
                      }
                  },
                  {
                      "host_path": {
                          "src_path": "/root/work",
                          "dest_path": "/home/mind",
                          "read_only": false
                      }
                  }
              ]
          }
      }

Sample Response
---------------

-  Successful response

   .. code-block::

      {
          "is_success": true,
          "job_id": "10",
          "job_name": "TestModelArtsJob",
          "status": "1",
          "create_time": "1524189990635",
          "version_id": "10",
          "version_name": "V0001",
          "resource_id": "jobafd08896"
      }

-  Failed response

   .. code-block::

      {
          "is_success": false,
          "error_message": "Job name:TestModelArtsJob is existed",
          "error_code": "ModelArts.0103"
      }

Status Code
-----------

For details about the status code, see :ref:`Status Code <modelarts_03_0094>`.
