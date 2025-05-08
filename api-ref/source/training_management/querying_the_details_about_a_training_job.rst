:original_name: ShowTrainingJobDetails.html

.. _ShowTrainingJobDetails:

Querying the Details About a Training Job
=========================================

Function
--------

This API is used to query the details about a training job.

URI
---

GET /v2/{project_id}/training-jobs/{training_job_id}

.. table:: **Table 1** Path Parameters

   +-----------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory | Type   | Description                                                                                                              |
   +=================+===========+========+==========================================================================================================================+
   | project_id      | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`.                                 |
   +-----------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | training_job_id | Yes       | String | Training job ID For details about how to obtain the value, see :ref:`Querying the Training Job List <listtrainingjobs>`. |
   +-----------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                                                          | Description                                                                                           |
   +=======================+===============================================================================================================================+=======================================================================================================+
   | kind                  | String                                                                                                                        | Training job type, which is **job** by default. Options:                                              |
   |                       |                                                                                                                               |                                                                                                       |
   |                       |                                                                                                                               | -  **job**: training job                                                                              |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | metadata              | :ref:`JobMetadata <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_jobmetadata>` object                   | Metadata of a training job.                                                                           |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | status                | :ref:`Status <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_status>` object                             | Status of a training job. You do not need to set this parameter when creating a job.                  |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | algorithm             | :ref:`JobAlgorithmResponse <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_jobalgorithmresponse>` object | Algorithm used by a training job. The options are as follows:                                         |
   |                       |                                                                                                                               |                                                                                                       |
   |                       |                                                                                                                               | -  **id**: Only the algorithm ID is used.                                                             |
   |                       |                                                                                                                               |                                                                                                       |
   |                       |                                                                                                                               | -  **subscription_id+item_version_id**: The subscription ID and version ID of the algorithm are used. |
   |                       |                                                                                                                               |                                                                                                       |
   |                       |                                                                                                                               | -  **code_dir+boot_file**: The code directory and boot file of the training job are used.             |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | tasks                 | Array of :ref:`TaskResponse <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_taskresponse>` objects       | List of tasks in heterogeneous training jobs.                                                         |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | spec                  | :ref:`SpecResponce <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_specresponce>` object                 | Specifications of a training job.                                                                     |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | endpoints             | :ref:`JobEndpointsResp <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_jobendpointsresp>` object         | This section describes the configurations required for remotely accessing a training job.             |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_jobmetadata:

.. table:: **Table 3** JobMetadata

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                              |
   +=======================+=======================+==========================================================================================================================================+
   | id                    | String                | Training job ID, which is generated and returned by ModelArts after the training job is created.                                         |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                | Name of a training job. The value must contain 1 to 64 characters consisting of only digits, letters, underscores (_), and hyphens (-).  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | workspace_id          | String                | Workspace where a job is located. The default value is **0**.                                                                            |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                | Training job description. The value must contain 0 to 256 characters. The default value is **NULL**.                                     |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time           | Long                  | Time when a training job was created, in milliseconds. The value is generated and returned by ModelArts after a training job is created. |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | user_name             | String                | Username for creating a training job. The username is generated and returned by ModelArts after a training job is created.               |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | annotations           | Map<String,String>    | Advanced configurations of a training job. The options are as follows:                                                                   |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  **job_template**: **Template RL** (heterogeneous job)                                                                                 |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  **fault-tolerance/job-retry-num**: **3** (number of retries upon a fault)                                                             |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  **fault-tolerance/job-unconditional-retry**: **true** (unconditional restart)                                                         |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  **fault-tolerance/hang-retry**: **true** (restart upon a suspension)                                                                  |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  **jupyter-lab/enable**: **true** (JupyterLab training application)                                                                    |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  **tensorboard/enable**: **true** (TensorBoard training application)                                                                   |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  **mindstudio-insight/enable**: **true** (MindStudio Insight training application)                                                     |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_status:

.. table:: **Table 4** Status

   +-----------------------+---------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                                                      | Description                                                                                                                                                    |
   +=======================+===========================================================================================================================+================================================================================================================================================================+
   | phase                 | String                                                                                                                    | Level-1 status of a training job. The options are:                                                                                                             |
   |                       |                                                                                                                           |                                                                                                                                                                |
   |                       |                                                                                                                           | -  Creating: The gateway is being created.                                                                                                                     |
   |                       |                                                                                                                           |                                                                                                                                                                |
   |                       |                                                                                                                           | -  Pending: waiting                                                                                                                                            |
   |                       |                                                                                                                           |                                                                                                                                                                |
   |                       |                                                                                                                           | -  Running                                                                                                                                                     |
   |                       |                                                                                                                           |                                                                                                                                                                |
   |                       |                                                                                                                           | -  Failed: The task fails to be executed.                                                                                                                      |
   |                       |                                                                                                                           |                                                                                                                                                                |
   |                       |                                                                                                                           | -  Completed: completed                                                                                                                                        |
   |                       |                                                                                                                           |                                                                                                                                                                |
   |                       |                                                                                                                           | -  Terminating: The task is being stopped.                                                                                                                     |
   |                       |                                                                                                                           |                                                                                                                                                                |
   |                       |                                                                                                                           | -  Terminated: stopped                                                                                                                                         |
   |                       |                                                                                                                           |                                                                                                                                                                |
   |                       |                                                                                                                           | -  Abnormal: abnormal                                                                                                                                          |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | secondary_phase       | String                                                                                                                    | The level-2 status of a training job is an internal detailed status, which may be added, modified, or deleted. Dependency is not recommended. The options are: |
   |                       |                                                                                                                           |                                                                                                                                                                |
   |                       |                                                                                                                           | -  Creating: The gateway is being created.                                                                                                                     |
   |                       |                                                                                                                           |                                                                                                                                                                |
   |                       |                                                                                                                           | -  Queuing: queuing                                                                                                                                            |
   |                       |                                                                                                                           |                                                                                                                                                                |
   |                       |                                                                                                                           | -  Running                                                                                                                                                     |
   |                       |                                                                                                                           |                                                                                                                                                                |
   |                       |                                                                                                                           | -  Failed: The task fails to be executed.                                                                                                                      |
   |                       |                                                                                                                           |                                                                                                                                                                |
   |                       |                                                                                                                           | -  Completed: completed                                                                                                                                        |
   |                       |                                                                                                                           |                                                                                                                                                                |
   |                       |                                                                                                                           | -  Terminating: The task is being stopped.                                                                                                                     |
   |                       |                                                                                                                           |                                                                                                                                                                |
   |                       |                                                                                                                           | -  Terminated: stopped                                                                                                                                         |
   |                       |                                                                                                                           |                                                                                                                                                                |
   |                       |                                                                                                                           | -  CreateFailed: The creation fails.                                                                                                                           |
   |                       |                                                                                                                           |                                                                                                                                                                |
   |                       |                                                                                                                           | -  TerminatedFailed: The service fails to be stopped.                                                                                                          |
   |                       |                                                                                                                           |                                                                                                                                                                |
   |                       |                                                                                                                           | -  Unknown: unknown status                                                                                                                                     |
   |                       |                                                                                                                           |                                                                                                                                                                |
   |                       |                                                                                                                           | -  Lost: abnormal                                                                                                                                              |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | duration              | Long                                                                                                                      | Running duration of a training job, in milliseconds                                                                                                            |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | node_count_metrics    | Array<Array<Integer>>                                                                                                     | Node count changes during the training job running period.                                                                                                     |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tasks                 | Array of strings                                                                                                          | Tasks of a training job.                                                                                                                                       |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | start_time            | Long                                                                                                                      | Start time of a training job. The value is in timestamp format.                                                                                                |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | task_statuses         | Array of :ref:`TaskStatuses <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_taskstatuses>` objects   | Status of a training job task.                                                                                                                                 |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | running_records       | Array of :ref:`RunningRecord <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_runningrecord>` objects | Running and fault recovery records of a training job                                                                                                           |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_taskstatuses:

.. table:: **Table 5** TaskStatuses

   ========= ======= =====================================
   Parameter Type    Description
   ========= ======= =====================================
   task      String  Task of a training job.
   exit_code Integer Exit code of a training job task.
   message   String  Error message of a training job task.
   ========= ======= =====================================

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_runningrecord:

.. table:: **Table 6** RunningRecord

   +------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                    | Type                  | Description                                                                                                                                                          |
   +==============================+=======================+======================================================================================================================================================================+
   | start_at                     | Integer               | Unix timestamp of the start time in the current running record, in seconds.                                                                                          |
   +------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | end_at                       | Integer               | Unix timestamp of the end time in the current running record, in seconds.                                                                                            |
   +------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | start_type                   | String                | Startup mode of the current running record.                                                                                                                          |
   |                              |                       |                                                                                                                                                                      |
   |                              |                       | -  **init_or_rescheduled**: This startup is the first running after scheduling, including the first startup and the running after scheduling recovery.               |
   |                              |                       |                                                                                                                                                                      |
   |                              |                       | -  **restarted**: This startup is not the first running after scheduling but the running after a process restart.                                                    |
   +------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | end_reason                   | String                | Reason why the current running record ends.                                                                                                                          |
   +------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | end_related_task             | String                | ID of the task worker that causes the end of the current running record, for example, **worker-0**.                                                                  |
   +------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | end_recover                  | String                | Fault tolerance policy used after the current running record ends. The enums are as follows:                                                                         |
   |                              |                       |                                                                                                                                                                      |
   |                              |                       | -  **npu_proc_restart**: NPU in-place hot recovery                                                                                                                   |
   |                              |                       |                                                                                                                                                                      |
   |                              |                       | -  **gpu_proc_restart**: GPU in-place hot recovery                                                                                                                   |
   |                              |                       |                                                                                                                                                                      |
   |                              |                       | -  **proc_restart**: Process in-place recovery                                                                                                                       |
   |                              |                       |                                                                                                                                                                      |
   |                              |                       | -  **pod_reschedule**: Pod-level rescheduling                                                                                                                        |
   |                              |                       |                                                                                                                                                                      |
   |                              |                       | -  **job_reschedule**: Job-level rescheduling                                                                                                                        |
   |                              |                       |                                                                                                                                                                      |
   |                              |                       | -  **job_reschedule_with_taint**: Isolated job-level rescheduling                                                                                                    |
   +------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | end_recover_before_downgrade | String                | Tolerance policy used after the current running record ends and before the fault tolerance policy is degraded. The options are the same as those of **end_recover**. |
   +------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_jobalgorithmresponse:

.. table:: **Table 7** JobAlgorithmResponse

   +---------------------------+-------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                 | Type                                                                                                              | Description                                                                                                                                                                                                                                                                    |
   +===========================+===================================================================================================================+================================================================================================================================================================================================================================================================================+
   | id                        | String                                                                                                            | Algorithm used by a training job. The options are as follows:                                                                                                                                                                                                                  |
   |                           |                                                                                                                   |                                                                                                                                                                                                                                                                                |
   |                           |                                                                                                                   | -  **id**: Only the algorithm ID is used.                                                                                                                                                                                                                                      |
   |                           |                                                                                                                   |                                                                                                                                                                                                                                                                                |
   |                           |                                                                                                                   | -  **subscription_id+item_version_id**: The subscription ID and version ID of the algorithm are used.                                                                                                                                                                          |
   |                           |                                                                                                                   |                                                                                                                                                                                                                                                                                |
   |                           |                                                                                                                   | -  **code_dir+boot_file**: The code directory and boot file of the training job are used.                                                                                                                                                                                      |
   +---------------------------+-------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                      | String                                                                                                            | Algorithm name.                                                                                                                                                                                                                                                                |
   +---------------------------+-------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | subscription_id           | String                                                                                                            | Subscription ID of a subscribed algorithm, which must be used with **item_version_id**                                                                                                                                                                                         |
   +---------------------------+-------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | item_version_id           | String                                                                                                            | Version ID of the subscribed algorithm, which must be used with **subscription_id**                                                                                                                                                                                            |
   +---------------------------+-------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | code_dir                  | String                                                                                                            | Code directory of a training job, for example, /usr/app/. This parameter must be set together with boot_file. If id or subscription_id+item_version_id has been set for boot_file, you do not need to set this parameter.                                                      |
   +---------------------------+-------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | boot_file                 | String                                                                                                            | Boot file of a training job, which needs to be stored in the code directory. for example, **/usr/app/boot.py**. This parameter must be used together with code_dir. If id or subscription_id+item_version_id has been set for code_dir, you do not need to set this parameter. |
   +---------------------------+-------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | autosearch_config_path    | String                                                                                                            | YAML configuration path of an auto search job. An OBS URL is required. For example, obs://bucket/file.yaml.                                                                                                                                                                    |
   +---------------------------+-------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | autosearch_framework_path | String                                                                                                            | Framework code directory of auto search jobs. An OBS URL is required. For example, obs://bucket/files/.                                                                                                                                                                        |
   +---------------------------+-------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | command                   | String                                                                                                            | Boot command for starting the container of a custom image for a training job. For example, **python train.py**.                                                                                                                                                                |
   +---------------------------+-------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | parameters                | Array of :ref:`Parameter <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_parameter>` objects | Running parameters of a training job.                                                                                                                                                                                                                                          |
   +---------------------------+-------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | policies                  | :ref:`policies <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_policies>` object             | Policies supported by jobs.                                                                                                                                                                                                                                                    |
   +---------------------------+-------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | inputs                    | Array of :ref:`Input <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_input>` objects         | Input of a training job.                                                                                                                                                                                                                                                       |
   +---------------------------+-------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | outputs                   | Array of :ref:`Output <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_output>` objects       | Output of a training job.                                                                                                                                                                                                                                                      |
   +---------------------------+-------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | engine                    | :ref:`JobEngine <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_jobengine>` object           | Engine of a training job. Leave this parameter blank if the job is created using **id** of the algorithm in algorithm management, or **subscription_id+item_version_id** of the subscribed algorithm.                                                                          |
   +---------------------------+-------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | local_code_dir            | String                                                                                                            | Local directory of the training container to which the algorithm code directory is downloaded. The rules are as follows:                                                                                                                                                       |
   |                           |                                                                                                                   |                                                                                                                                                                                                                                                                                |
   |                           |                                                                                                                   | -  The directory must be under **/home**.                                                                                                                                                                                                                                      |
   |                           |                                                                                                                   |                                                                                                                                                                                                                                                                                |
   |                           |                                                                                                                   | -  In v1 compatibility mode, the current field does not take effect.                                                                                                                                                                                                           |
   |                           |                                                                                                                   |                                                                                                                                                                                                                                                                                |
   |                           |                                                                                                                   | -  When **code_dir** is prefixed with **file://**, the current field does not take effect.                                                                                                                                                                                     |
   +---------------------------+-------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | working_dir               | String                                                                                                            | Work directory where an algorithm is executed. Note that this parameter does not take effect in v1 compatibility mode.                                                                                                                                                         |
   +---------------------------+-------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | environments              | Array of Map<String,String> objects                                                                               | Environment variables of a training job. The format is **key:value**. Leave this parameter blank.                                                                                                                                                                              |
   +---------------------------+-------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | summary                   | :ref:`Summary <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_summary>` object               | Visualization log summary.                                                                                                                                                                                                                                                     |
   +---------------------------+-------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_parameter:

.. table:: **Table 8** Parameter

   +------------------+-----------------------------------------------------------------------------------------------------------------------+-----------------------------------+
   | Parameter        | Type                                                                                                                  | Description                       |
   +==================+=======================================================================================================================+===================================+
   | name             | String                                                                                                                | Parameter name.                   |
   +------------------+-----------------------------------------------------------------------------------------------------------------------+-----------------------------------+
   | value            | String                                                                                                                | Parameter value.                  |
   +------------------+-----------------------------------------------------------------------------------------------------------------------+-----------------------------------+
   | description      | String                                                                                                                | Parameter description.            |
   +------------------+-----------------------------------------------------------------------------------------------------------------------+-----------------------------------+
   | constraint       | :ref:`constraint <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_constraint>` object             | Parameter constraint.             |
   +------------------+-----------------------------------------------------------------------------------------------------------------------+-----------------------------------+
   | i18n_description | :ref:`i18n_description <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_i18n_description>` object | Internationalization description. |
   +------------------+-----------------------------------------------------------------------------------------------------------------------+-----------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_constraint:

.. table:: **Table 9** constraint

   +-------------+------------------+--------------------------------------------------------------------------------+
   | Parameter   | Type             | Description                                                                    |
   +=============+==================+================================================================================+
   | type        | String           | Parameter type.                                                                |
   +-------------+------------------+--------------------------------------------------------------------------------+
   | editable    | Boolean          | Whether the parameter is editable.                                             |
   +-------------+------------------+--------------------------------------------------------------------------------+
   | required    | Boolean          | Whether the parameter is mandatory.                                            |
   +-------------+------------------+--------------------------------------------------------------------------------+
   | sensitive   | Boolean          | Whether the parameter is sensitive This function is not implemented currently. |
   +-------------+------------------+--------------------------------------------------------------------------------+
   | valid_type  | String           | Valid type.                                                                    |
   +-------------+------------------+--------------------------------------------------------------------------------+
   | valid_range | Array of strings | Valid range.                                                                   |
   +-------------+------------------+--------------------------------------------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_i18n_description:

.. table:: **Table 10** i18n_description

   =========== ====== =========================================
   Parameter   Type   Description
   =========== ====== =========================================
   language    String International language.
   description String Description of an international language.
   =========== ====== =========================================

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_policies:

.. table:: **Table 11** policies

   +-------------+-------------------------------------------------------------------------------------------------------------+--------------------------------------+
   | Parameter   | Type                                                                                                        | Description                          |
   +=============+=============================================================================================================+======================================+
   | auto_search | :ref:`auto_search <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_auto_search>` object | Hyperparameter search configuration. |
   +-------------+-------------------------------------------------------------------------------------------------------------+--------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_auto_search:

.. table:: **Table 12** auto_search

   +--------------------+---------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------+
   | Parameter          | Type                                                                                                                      | Description                                        |
   +====================+===========================================================================================================================+====================================================+
   | skip_search_params | String                                                                                                                    | Hyperparameter parameters that need to be skipped. |
   +--------------------+---------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------+
   | reward_attrs       | Array of :ref:`reward_attrs <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_reward_attrs>` objects   | List of search metrics.                            |
   +--------------------+---------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------+
   | search_params      | Array of :ref:`search_params <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_search_params>` objects | Search parameters.                                 |
   +--------------------+---------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------+
   | algo_configs       | Array of :ref:`algo_configs <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_algo_configs>` objects   | Search algorithm configurations.                   |
   +--------------------+---------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_reward_attrs:

.. table:: **Table 13** reward_attrs

   +-----------------------+-----------------------+--------------------------------------------------+
   | Parameter             | Type                  | Description                                      |
   +=======================+=======================+==================================================+
   | name                  | String                | Metric name.                                     |
   +-----------------------+-----------------------+--------------------------------------------------+
   | mode                  | String                | Search mode.                                     |
   |                       |                       |                                                  |
   |                       |                       | -  **max**: A larger metric value is preferred.  |
   |                       |                       |                                                  |
   |                       |                       | -  **min**: A smaller metric value is preferred. |
   +-----------------------+-----------------------+--------------------------------------------------+
   | regex                 | String                | Regular expression of a metric.                  |
   +-----------------------+-----------------------+--------------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_search_params:

.. table:: **Table 14** search_params

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                          |
   +=======================+=======================+======================================================================================================================================================================================+
   | name                  | String                | Hyperparameter name.                                                                                                                                                                 |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | param_type            | String                | Parameter type.                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                                      |
   |                       |                       | -  **continuous**: The hyperparameter is of the continuous type. When an algorithm is used in a training job, continuous hyperparameters are displayed as text boxes on the console. |
   |                       |                       |                                                                                                                                                                                      |
   |                       |                       | -  **discrete**: The hyperparameter is of the discrete type. When an algorithm is used in a training job, discrete hyperparameters are displayed as drop-down lists on the console.  |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | lower_bound           | String                | Lower bound of the hyperparameter.                                                                                                                                                   |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | upper_bound           | String                | Upper bound of the hyperparameter.                                                                                                                                                   |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | discrete_points_num   | String                | Number of discrete points of a continuous hyperparameter.                                                                                                                            |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | discrete_values       | Array of strings      | List of discrete hyperparameter values.                                                                                                                                              |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_algo_configs:

.. table:: **Table 15** algo_configs

   +-----------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------+
   | Parameter | Type                                                                                                                                                      | Description                   |
   +===========+===========================================================================================================================================================+===============================+
   | name      | String                                                                                                                                                    | Name of the search algorithm. |
   +-----------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------+
   | params    | Array of :ref:`AutoSearchAlgoConfigParameter <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_autosearchalgoconfigparameter>` objects | Search algorithm parameters.  |
   +-----------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_autosearchalgoconfigparameter:

.. table:: **Table 16** AutoSearchAlgoConfigParameter

   ========= ====== ================
   Parameter Type   Description
   ========= ====== ================
   key       String Parameter key.
   value     String Parameter value.
   type      String Parameter type.
   ========= ====== ================

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_input:

.. table:: **Table 17** Input

   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                                                              | Description                                                                                                                    |
   +=======================+===================================================================================================================================+================================================================================================================================+
   | name                  | String                                                                                                                            | Name of the data input channel.                                                                                                |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                                                                                                                            | Description of the data input channel.                                                                                         |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | local_dir             | String                                                                                                                            | Local directory of the container to which the data input channel is mapped Example: /home/ma-user/modelarts/inputs/data_url_0. |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | remote                | :ref:`InputDataInfo <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_inputdatainfo>` object                   | Information of the data input. Enums:                                                                                          |
   |                       |                                                                                                                                   |                                                                                                                                |
   |                       |                                                                                                                                   | -  **dataset**: The data input is a dataset.                                                                                   |
   |                       |                                                                                                                                   |                                                                                                                                |
   |                       |                                                                                                                                   | -  **obs**: The data input is an OBS path.                                                                                     |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | remote_constraint     | Array of :ref:`remote_constraint <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_remote_constraint>` objects | Data input constraint                                                                                                          |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_inputdatainfo:

.. table:: **Table 18** InputDataInfo

   +-----------+-----------------------------------------------------------------------------------------------------+--------------------------------------------+
   | Parameter | Type                                                                                                | Description                                |
   +===========+=====================================================================================================+============================================+
   | dataset   | :ref:`dataset <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_dataset>` object | Dataset as the data input.                 |
   +-----------+-----------------------------------------------------------------------------------------------------+--------------------------------------------+
   | obs       | :ref:`obs <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_obs>` object         | OBS in which data input and output stored. |
   +-----------+-----------------------------------------------------------------------------------------------------+--------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_dataset:

.. table:: **Table 19** dataset

   +------------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Type   | Description                                                                                                                                                     |
   +============+========+=================================================================================================================================================================+
   | id         | String | Dataset ID of a training job.                                                                                                                                   |
   +------------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version_id | String | Dataset version ID of a training job.                                                                                                                           |
   +------------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | obs_url    | String | OBS URL of the dataset for a training job. It is automatically parsed by ModelArts based on the dataset ID and dataset version ID. For example, **/usr/data/**. |
   +------------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_obs:

.. table:: **Table 20** obs

   +-----------+--------+---------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                     |
   +===========+========+=================================================================================+
   | obs_url   | String | OBS URL of the dataset required by a training job. For example, **/usr/data/**. |
   +-----------+--------+---------------------------------------------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_remote_constraint:

.. table:: **Table 21** remote_constraint

   +-----------------------+-----------------------+-------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                       |
   +=======================+=======================+===================================================================+
   | data_type             | String                | Data input type, including the data storage location and dataset. |
   +-----------------------+-----------------------+-------------------------------------------------------------------+
   | attributes            | String                | Attributes if a dataset is used as the data input. Options:       |
   |                       |                       |                                                                   |
   |                       |                       | -  **data_format**: Data format                                   |
   |                       |                       |                                                                   |
   |                       |                       | -  **data_segmentation**: Data segmentation                       |
   |                       |                       |                                                                   |
   |                       |                       | -  **dataset_type**: Labeling type                                |
   +-----------------------+-----------------------+-------------------------------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_output:

.. table:: **Table 22** Output

   +-------------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | Parameter   | Type                                                                                              | Description                                                                  |
   +=============+===================================================================================================+==============================================================================+
   | name        | String                                                                                            | Name of the data output channel.                                             |
   +-------------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | description | String                                                                                            | Description of the data output channel.                                      |
   +-------------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | local_dir   | String                                                                                            | Local directory of the container to which the data output channel is mapped. |
   +-------------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | remote      | :ref:`Remote <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_remote>` object | Description of the actual data output.                                       |
   +-------------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_jobengine:

.. table:: **Table 23** JobEngine

   +----------------------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter            | Type    | Description                                                                                                                                                                                                                                   |
   +======================+=========+===============================================================================================================================================================================================================================================+
   | engine_id            | String  | Engine ID selected for a training job. The value can be **engine_id**, **engine_name + engine_version**, or **image_url**.                                                                                                                    |
   +----------------------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | engine_name          | String  | Name of the engine selected for a training job. If **engine_id** has been set, you do not need to set this parameter.                                                                                                                         |
   +----------------------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | engine_version       | String  | Version of the engine selected for a training job. If **engine_id** has been set, you do not need to set this parameter.                                                                                                                      |
   +----------------------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | image_url            | String  | Custom image URL selected for a training job. The URL is obtained from SWR.                                                                                                                                                                   |
   +----------------------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | install_sys_packages | Boolean | Whether to install the MoXing version specified by the training platform. Value **true** means to install the specified MoXing version. This parameter is available only when **engine_name**, **engine_version**, and **image_url** are set. |
   +----------------------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_summary:

.. table:: **Table 24** Summary

   +-----------------------+---------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                                                | Description                                                                                                                                                                                                        |
   +=======================+=====================================================================================================================+====================================================================================================================================================================================================================+
   | log_type              | String                                                                                                              | Visualization log type of a training job. After this parameter is configured, the training job can be used as the data source of a visualization job. The options are as follows:                                  |
   |                       |                                                                                                                     |                                                                                                                                                                                                                    |
   |                       |                                                                                                                     | -  **tensorboard**                                                                                                                                                                                                 |
   |                       |                                                                                                                     |                                                                                                                                                                                                                    |
   |                       |                                                                                                                     | -  **mindstudio-insight**                                                                                                                                                                                          |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_dir               | :ref:`LogDir <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_logdir>` object                   | Visualization log output of a training job. This parameter is mandatory when **log_type** is not empty.                                                                                                            |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | data_sources          | Array of :ref:`DataSource <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_datasource>` objects | Visualization log input of a visualization job or debug training job. This parameter is mandatory when **tensorboard/enable** or **mindstudio-insight/enable** is set to **true** for advanced training functions. |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_logdir:

.. table:: **Table 25** LogDir

   +-----------+-----------------------------------------------------------------------------------------------------------+----------------------------------------+
   | Parameter | Type                                                                                                      | Description                            |
   +===========+===========================================================================================================+========================================+
   | pfs       | :ref:`PFSSummary <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_pfssummary>` object | Output of an OBS parallel file system. |
   +-----------+-----------------------------------------------------------------------------------------------------------+----------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_pfssummary:

.. table:: **Table 26** PFSSummary

   ========= ====== ===================================
   Parameter Type   Description
   ========= ====== ===================================
   pfs_path  String URL of an OBS parallel file system.
   ========= ====== ===================================

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_datasource:

.. table:: **Table 27** DataSource

   +-----------+-----------------------------------------------------------------------------------------------------------+------------------+
   | Parameter | Type                                                                                                      | Description      |
   +===========+===========================================================================================================+==================+
   | job       | :ref:`JobSummary <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_jobsummary>` object | Job data source. |
   +-----------+-----------------------------------------------------------------------------------------------------------+------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_jobsummary:

.. table:: **Table 28** JobSummary

   ========= ====== ================
   Parameter Type   Description
   ========= ====== ================
   job_id    String Training job ID.
   ========= ====== ================

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_taskresponse:

.. table:: **Table 29** TaskResponse

   +---------------+---------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------+
   | Parameter     | Type                                                                                                                            | Description                                          |
   +===============+=================================================================================================================================+======================================================+
   | role          | String                                                                                                                          | Task role. This function is not supported currently. |
   +---------------+---------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------+
   | algorithm     | :ref:`TaskResponseAlgorithm <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_taskresponsealgorithm>` object | Algorithm management and configuration.              |
   +---------------+---------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------+
   | task_resource | :ref:`FlavorResponse <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_flavorresponse>` object               | Flavors of a training job or an algorithm.           |
   +---------------+---------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_taskresponsealgorithm:

.. table:: **Table 30** TaskResponseAlgorithm

   +-----------------------+---------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                                                | Description                                                                                                              |
   +=======================+=====================================================================================================================+==========================================================================================================================+
   | code_dir              | String                                                                                                              | Absolute path of the directory where the algorithm boot file is stored.                                                  |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------+
   | boot_file             | String                                                                                                              | Absolute path of the algorithm boot file.                                                                                |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------+
   | inputs                | :ref:`AlgorithmInput <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_algorithminput>` object   | Algorithm input channel.                                                                                                 |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------+
   | outputs               | :ref:`AlgorithmOutput <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_algorithmoutput>` object | Algorithm output channel.                                                                                                |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------+
   | engine                | :ref:`AlgorithmEngine <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_algorithmengine>` object | Engine on which a heterogeneous job depends.                                                                             |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------+
   | local_code_dir        | String                                                                                                              | Local directory of the training container to which the algorithm code directory is downloaded. The rules are as follows: |
   |                       |                                                                                                                     |                                                                                                                          |
   |                       |                                                                                                                     | -  The directory must be under **/home**.                                                                                |
   |                       |                                                                                                                     |                                                                                                                          |
   |                       |                                                                                                                     | -  In v1 compatibility mode, the current field does not take effect.                                                     |
   |                       |                                                                                                                     |                                                                                                                          |
   |                       |                                                                                                                     | -  When **code_dir** is prefixed with **file://**, the current field does not take effect.                               |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------+
   | working_dir           | String                                                                                                              | Work directory where an algorithm is executed. Note that this parameter does not take effect in v1 compatibility mode.   |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_algorithminput:

.. table:: **Table 31** AlgorithmInput

   +-----------+---------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------+
   | Parameter | Type                                                                                                                | Description                                                                         |
   +===========+=====================================================================================================================+=====================================================================================+
   | name      | String                                                                                                              | Name of the data input channel.                                                     |
   +-----------+---------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------+
   | local_dir | String                                                                                                              | Local path of the container to which the data input and output channels are mapped. |
   +-----------+---------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------+
   | remote    | :ref:`AlgorithmRemote <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_algorithmremote>` object | Actual data input, which can only be OBS for heterogeneous jobs.                    |
   +-----------+---------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_algorithmremote:

.. table:: **Table 32** AlgorithmRemote

   +-----------+---------------------------------------------------------------------------------------------------------+------------------------------------------------+
   | Parameter | Type                                                                                                    | Description                                    |
   +===========+=========================================================================================================+================================================+
   | obs       | :ref:`RemoteObs <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_remoteobs>` object | OBS in which data input and output are stored. |
   +-----------+---------------------------------------------------------------------------------------------------------+------------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_algorithmoutput:

.. table:: **Table 33** AlgorithmOutput

   +-----------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | Parameter | Type                                                                                              | Description                                                                  |
   +===========+===================================================================================================+==============================================================================+
   | name      | String                                                                                            | Name of the data output channel.                                             |
   +-----------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | local_dir | String                                                                                            | Local directory of the container to which the data output channel is mapped. |
   +-----------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | remote    | :ref:`Remote <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_remote>` object | Description of the actual data output.                                       |
   +-----------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | mode      | String                                                                                            | Data transmission mode. The default value is **upload_periodically**.        |
   +-----------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | period    | String                                                                                            | Data transmission period. The default value is **30s**.                      |
   +-----------+---------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_remote:

.. table:: **Table 34** Remote

   +-----------+---------------------------------------------------------------------------------------------------------+-----------------------------------------+
   | Parameter | Type                                                                                                    | Description                             |
   +===========+=========================================================================================================+=========================================+
   | obs       | :ref:`RemoteObs <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_remoteobs>` object | OBS to which data is actually exported. |
   +-----------+---------------------------------------------------------------------------------------------------------+-----------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_remoteobs:

.. table:: **Table 35** RemoteObs

   ========= ====== ==================================
   Parameter Type   Description
   ========= ====== ==================================
   obs_url   String OBS URL to which data is exported.
   ========= ====== ==================================

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_algorithmengine:

.. table:: **Table 36** AlgorithmEngine

   +----------------+---------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter      | Type    | Description                                                                                                              |
   +================+=========+==========================================================================================================================+
   | engine_id      | String  | Engine ID, for example, **caffe-1.0.0-python2.7**.                                                                       |
   +----------------+---------+--------------------------------------------------------------------------------------------------------------------------+
   | engine_name    | String  | Engine name, for example, **Caffe**.                                                                                     |
   +----------------+---------+--------------------------------------------------------------------------------------------------------------------------+
   | engine_version | String  | Engine version. Engines with the same name have multiple versions, for example, **Caffe-1.0.0-python2.7** of Python 2.7. |
   +----------------+---------+--------------------------------------------------------------------------------------------------------------------------+
   | v1_compatible  | Boolean | Whether the v1 compatibility mode is used.                                                                               |
   +----------------+---------+--------------------------------------------------------------------------------------------------------------------------+
   | run_user       | String  | User UID started by default by the engine.                                                                               |
   +----------------+---------+--------------------------------------------------------------------------------------------------------------------------+
   | image_url      | String  | Custom image URL selected for an algorithm.                                                                              |
   +----------------+---------+--------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_flavorresponse:

.. table:: **Table 37** FlavorResponse

   +-----------------------+---------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------+
   | Parameter             | Type                                                                                                                      | Description                                   |
   +=======================+===========================================================================================================================+===============================================+
   | flavor_id             | String                                                                                                                    | ID of the resource flavor.                    |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------+
   | flavor_name           | String                                                                                                                    | Name of the resource flavor.                  |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------+
   | max_num               | Integer                                                                                                                   | Maximum number of nodes in a resource flavor. |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------+
   | flavor_type           | String                                                                                                                    | Resource flavor type. Options:                |
   |                       |                                                                                                                           |                                               |
   |                       |                                                                                                                           | -  **CPU**                                    |
   |                       |                                                                                                                           |                                               |
   |                       |                                                                                                                           | -  **GPU**                                    |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------+
   | billing               | :ref:`BillingInfo <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_billinginfo>` object               | Billing information of a resource flavor.     |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------+
   | flavor_info           | :ref:`FlavorInfoResponse <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_flavorinforesponse>` object | Resource flavor details.                      |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------+
   | attributes            | Map<String,String>                                                                                                        | Other specification attributes.               |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_flavorinforesponse:

.. table:: **Table 38** FlavorInfoResponse

   +-----------+---------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type                                                                                                          | Description                                                                                                         |
   +===========+===============================================================================================================+=====================================================================================================================+
   | max_num   | Integer                                                                                                       | Maximum number of nodes that can be selected. The value **1** indicates that the distributed mode is not supported. |
   +-----------+---------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | cpu       | :ref:`Cpu <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_cpu>` object                   | CPU specifications.                                                                                                 |
   +-----------+---------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | gpu       | :ref:`Gpu <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_gpu>` object                   | GPU specifications.                                                                                                 |
   +-----------+---------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | memory    | :ref:`Memory <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_memory>` object             | Memory information.                                                                                                 |
   +-----------+---------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | disk      | :ref:`DiskResponse <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_diskresponse>` object | Disk information.                                                                                                   |
   +-----------+---------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_diskresponse:

.. table:: **Table 39** DiskResponse

   ========= ======= ======================
   Parameter Type    Description
   ========= ======= ======================
   size      Integer Disk size.
   unit      String  Unit of the disk size.
   ========= ======= ======================

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_specresponce:

.. table:: **Table 40** SpecResponce

   +-----------------+---------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------+
   | Parameter       | Type                                                                                                                      | Description                                                                                 |
   +=================+===========================================================================================================================+=============================================================================================+
   | resource        | :ref:`Resource <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_resource>` object                     | Resource flavors of a training job. Select either **flavor_id** or **pool_id+[flavor_id]**. |
   +-----------------+---------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------+
   | volumes         | Array of :ref:`JobVolume <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_jobvolume>` objects         | Volumes attached for a training job.                                                        |
   +-----------------+---------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------+
   | log_export_path | :ref:`LogExportPath <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_logexportpath>` object           | Export path of training job logs.                                                           |
   +-----------------+---------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------+
   | schedule_policy | :ref:`SchedulePolicy <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_schedulepolicy>` object         | Training job scheduling policy.                                                             |
   +-----------------+---------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------+
   | custom_metrics  | Array of :ref:`CustomMetrics <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_custommetrics>` objects | Metric collection configuration                                                             |
   +-----------------+---------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_resource:

.. table:: **Table 41** Resource

   +-----------------------+---------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                                          | Description                                                                                                                                                                                                                     |
   +=======================+===============================================================================================================+=================================================================================================================================================================================================================================+
   | policy                | String                                                                                                        | Resource specification mode of a training job. The value can be regular, indicating the standard mode.                                                                                                                          |
   +-----------------------+---------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | flavor_id             | String                                                                                                        | ID of the resource flavor selected for a training job. **flavor_id** cannot be specified for dedicated resource pools with CPU specifications. The options for dedicated resource pools with GPU specifications are as follows: |
   |                       |                                                                                                               |                                                                                                                                                                                                                                 |
   |                       |                                                                                                               | -  **modelarts.pool.visual.xlarge** (1 card)                                                                                                                                                                                    |
   |                       |                                                                                                               |                                                                                                                                                                                                                                 |
   |                       |                                                                                                               | -  **modelarts.pool.visual.2xlarge** (2 cards)                                                                                                                                                                                  |
   |                       |                                                                                                               |                                                                                                                                                                                                                                 |
   |                       |                                                                                                               | -  **modelarts.pool.visual.4xlarge** (4 cards)                                                                                                                                                                                  |
   |                       |                                                                                                               |                                                                                                                                                                                                                                 |
   |                       |                                                                                                               | -  **modelarts.pool.visual.8xlarge** (8 cards)                                                                                                                                                                                  |
   +-----------------------+---------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | flavor_name           | String                                                                                                        | Read-only flavor name returned by ModelArts when **flavor_id** is used.                                                                                                                                                         |
   +-----------------------+---------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | node_count            | Integer                                                                                                       | Number of resource replicas selected for a training job.                                                                                                                                                                        |
   +-----------------------+---------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | pool_id               | String                                                                                                        | Resource pool ID selected for a training job.                                                                                                                                                                                   |
   +-----------------------+---------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | flavor_detail         | :ref:`FlavorDetail <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_flavordetail>` object | Flavor details of a training job or algorithm. This parameter is available only for public resource pools.                                                                                                                      |
   +-----------------------+---------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_flavordetail:

.. table:: **Table 42** FlavorDetail

   +-----------------------+-------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | Parameter             | Type                                                                                                        | Description                                       |
   +=======================+=============================================================================================================+===================================================+
   | flavor_type           | String                                                                                                      | Resource flavor type. The options are as follows: |
   |                       |                                                                                                             |                                                   |
   |                       |                                                                                                             | -  **CPU**                                        |
   |                       |                                                                                                             |                                                   |
   |                       |                                                                                                             | -  **GPU**                                        |
   +-----------------------+-------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | billing               | :ref:`BillingInfo <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_billinginfo>` object | Billing information of a resource flavor.         |
   +-----------------------+-------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | flavor_info           | :ref:`FlavorInfo <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_flavorinfo>` object   | Resource flavor details.                          |
   +-----------------------+-------------------------------------------------------------------------------------------------------------+---------------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_billinginfo:

.. table:: **Table 43** BillingInfo

   ========= ======= =============
   Parameter Type    Description
   ========= ======= =============
   code      String  Billing code.
   unit_num  Integer Billing unit.
   ========= ======= =============

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_flavorinfo:

.. table:: **Table 44** FlavorInfo

   +-----------+---------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type                                                                                              | Description                                                                                                         |
   +===========+===================================================================================================+=====================================================================================================================+
   | max_num   | Integer                                                                                           | Maximum number of nodes that can be selected. The value **1** indicates that the distributed mode is not supported. |
   +-----------+---------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | cpu       | :ref:`Cpu <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_cpu>` object       | CPU specifications.                                                                                                 |
   +-----------+---------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | gpu       | :ref:`Gpu <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_gpu>` object       | GPU specifications.                                                                                                 |
   +-----------+---------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | memory    | :ref:`Memory <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_memory>` object | Memory information.                                                                                                 |
   +-----------+---------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | disk      | :ref:`Disk <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_disk>` object     | Disk information.                                                                                                   |
   +-----------+---------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_cpu:

.. table:: **Table 45** Cpu

   ========= ======= =================
   Parameter Type    Description
   ========= ======= =================
   arch      String  CPU architecture.
   core_num  Integer Number of cores.
   ========= ======= =================

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_gpu:

.. table:: **Table 46** Gpu

   ============ ======= ===============
   Parameter    Type    Description
   ============ ======= ===============
   unit_num     Integer Number of GPUs.
   product_name String  Product name.
   memory       String  Memory.
   ============ ======= ===============

.. table:: **Table 47** Npu

   ============ ====== ===============
   Parameter    Type   Description
   ============ ====== ===============
   unit_num     String Number of NPUs.
   product_name String Product name.
   memory       String Memory.
   ============ ====== ===============

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_memory:

.. table:: **Table 48** Memory

   ========= ======= =======================
   Parameter Type    Description
   ========= ======= =======================
   size      Integer Memory size.
   unit      String  Number of memory units.
   ========= ======= =======================

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_disk:

.. table:: **Table 49** Disk

   ========= ====== =============================================
   Parameter Type   Description
   ========= ====== =============================================
   size      String Disk size.
   unit      String Unit of the disk size, which is GB generally.
   ========= ====== =============================================

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_jobvolume:

.. table:: **Table 50** JobVolume

   +-----------+---------------------------------------------------------------------------------------------+-------------------------------+
   | Parameter | Type                                                                                        | Description                   |
   +===========+=============================================================================================+===============================+
   | nfs       | :ref:`Nfs <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_nfs>` object | Volumes attached in NFS mode. |
   +-----------+---------------------------------------------------------------------------------------------+-------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_nfs:

.. table:: **Table 51** Nfs

   +-----------------+---------+---------------------------------------------------------------------------------------+
   | Parameter       | Type    | Description                                                                           |
   +=================+=========+=======================================================================================+
   | nfs_server_path | String  | NFS server path, for example, **10.10.10.10:/example/path**.                          |
   +-----------------+---------+---------------------------------------------------------------------------------------+
   | local_path      | String  | Path for attaching volumes to the training container, for example, **/example/path**. |
   +-----------------+---------+---------------------------------------------------------------------------------------+
   | read_only       | Boolean | Whether the disks attached to the container in NFS mode are read-only.                |
   +-----------------+---------+---------------------------------------------------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_logexportpath:

.. table:: **Table 52** LogExportPath

   +-----------+--------+--------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                          |
   +===========+========+======================================================================================+
   | obs_url   | String | OBS path for storing training job logs, for example, **obs://example/path**.         |
   +-----------+--------+--------------------------------------------------------------------------------------+
   | host_path | String | Path of the host where training job logs are stored, for example, **/example/path**. |
   +-----------+--------+--------------------------------------------------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_schedulepolicy:

.. table:: **Table 53** SchedulePolicy

   +-------------------+-----------------------------------------------------------------------------------------------------------------------+------------------------------------------+
   | Parameter         | Type                                                                                                                  | Description                              |
   +===================+=======================================================================================================================+==========================================+
   | required_affinity | :ref:`RequiredAffinity <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_requiredaffinity>` object | Affinity requirements for training jobs. |
   +-------------------+-----------------------------------------------------------------------------------------------------------------------+------------------------------------------+
   | priority          | Integer                                                                                                               | Priority of the training job.            |
   +-------------------+-----------------------------------------------------------------------------------------------------------------------+------------------------------------------+
   | preemptible       | Boolean                                                                                                               | Whether preemption is allowed            |
   +-------------------+-----------------------------------------------------------------------------------------------------------------------+------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_requiredaffinity:

.. table:: **Table 54** RequiredAffinity

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                                  |
   +=======================+=======================+==============================================================================================================================================================================================================================+
   | affinity_type         | String                | Affinity scheduling policy. Possible values are as follows:                                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                                                                              |
   |                       |                       | -  **cabinet**: strong cabinet scheduling                                                                                                                                                                                    |
   |                       |                       |                                                                                                                                                                                                                              |
   |                       |                       | -  **hyperinstance**: supernode affinity scheduling                                                                                                                                                                          |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | affinity_group_size   | Integer               | Affinity group size. This parameter is mandatory when **affinity_type** is set to **hyperinstance**. In this case, the system schedules tasks specified by **affinity_group_size** to a supernode to form an affinity group. |
   |                       |                       |                                                                                                                                                                                                                              |
   |                       |                       | When a user delivers a training job to the supernode resource pool, if the affinity group size is not set, the system sets the value to **1** by default.                                                                    |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_custommetrics:

.. table:: **Table 55** CustomMetrics

   +--------------+---------+-----------------------------------------------------------------------------------+
   | Parameter    | Type    | Description                                                                       |
   +==============+=========+===================================================================================+
   | metrics_url  | String  | URL for collecting metrics. Either configure all ports or leave all ports blank.  |
   +--------------+---------+-----------------------------------------------------------------------------------+
   | metrics_port | Integer | Port for collecting metrics. Either configure all ports or leave all ports blank. |
   +--------------+---------+-----------------------------------------------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_jobendpointsresp:

.. table:: **Table 56** JobEndpointsResp

   +--------------------+-------------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | Parameter          | Type                                                                                                                    | Description                                |
   +====================+=========================================================================================================================+============================================+
   | ssh                | :ref:`SSHResp <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_sshresp>` object                     | SSH connection information.                |
   +--------------------+-------------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | jupyter_lab        | :ref:`JupyterLab <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_jupyterlab>` object               | JupyterLab connection information.         |
   +--------------------+-------------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | tensorboard        | :ref:`Tensorboard <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_tensorboard>` object             | TensorBoard connection information.        |
   +--------------------+-------------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | mindstudio_insight | :ref:`MindStudioInsight <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_mindstudioinsight>` object | MindStudio Insight connection information. |
   +--------------------+-------------------------------------------------------------------------------------------------------------------------+--------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_sshresp:

.. table:: **Table 57** SSHResp

   +----------------+-----------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------+
   | Parameter      | Type                                                                                                            | Description                                                                                               |
   +================+=================================================================================================================+===========================================================================================================+
   | key_pair_names | Array of strings                                                                                                | Specifies the SSH key pair name, which can be created and viewed on the Key Pair page of the ECS console. |
   +----------------+-----------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------+
   | task_urls      | Array of :ref:`TaskUrls <en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_taskurls>` objects | SSH connection address information.                                                                       |
   +----------------+-----------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_taskurls:

.. table:: **Table 58** TaskUrls

   ========= ====== =========================================
   Parameter Type   Description
   ========= ====== =========================================
   task      String ID of a training job.
   url       String SSH connection address of a training job.
   ========= ====== =========================================

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_jupyterlab:

.. table:: **Table 59** JupyterLab

   ========= ====== =====================================
   Parameter Type   Description
   ========= ====== =====================================
   url       String JupyterLab address of a training job.
   token     String JupyterLab token of a training job.
   ========= ====== =====================================

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_tensorboard:

.. table:: **Table 60** Tensorboard

   ========= ====== ===================================
   Parameter Type   Description
   ========= ====== ===================================
   url       String TensorBoard URL of a training job.
   token     String TensorBoard token of a training job
   ========= ====== ===================================

.. _en-us_topic_0000002233886842__en-us_topic_0000002091282809_response_mindstudioinsight:

.. table:: **Table 61** MindStudioInsight

   ========= ====== ===========================================
   Parameter Type   Description
   ========= ====== ===========================================
   url       String MindStudio Insight URL of a training job.
   token     String MindStudio Insight token of a training job.
   ========= ====== ===========================================

Example Requests
----------------

The following shows how to query a training job whose UUID is **3faf5c03-aaa1-4cbe-879d-24b05d997347**.

.. code-block:: text

   GET https://endpoint/v2/{project_id}/training-jobs/3faf5c03-aaa1-4cbe-879d-24b05d997347

Example Responses
-----------------

**Status code: 200**

ok

.. code-block::

   {
     "kind" : "job",
     "metadata" : {
       "id" : "3faf5c03-aaa1-4cbe-879d-24b05d997347",
       "name" : "trainjob--py14_mem06-108",
       "description" : "",
       "create_time" : 1636447346315,
       "workspace_id" : "0",
       "user_name" : ""
     },
     "status" : {
       "phase" : "Abnormal",
       "secondary_phase" : "CreateFailed",
       "duration" : 0,
       "start_time" : 0,
       "node_count_metrics" : [ [ 1636447746000, 0 ], [ 1636447755000, 0 ], [ 1636447756000, 0 ] ],
       "tasks" : [ "worker-0" ],
       "running_records" : [ {
         "start_at" : 1701327093,
         "end_at" : 1701322341,
         "start_type" : "init_or_rescheduled",
         "end_recover" : "job_reschedule",
         "end_reason" : "exit with 127",
         "end_related_task" : "worker-2",
         "end_recover_before_downgrade" : "npu_proc_restart"
       }, {
         "start_at" : 1701323345,
         "end_at" : 1701325432,
         "start_type" : "init_or_rescheduled",
         "end_reason" : "job completed"
       } ]
     },
     "algorithm" : {
       "code_dir" : "obs://test/economic_test/py_minist/",
       "boot_file" : "obs://test/economic_test/py_minist/minist_common.py",
       "inputs" : [ {
         "name" : "data_url",
         "local_dir" : "/home/ma-user/modelarts/inputs/data_url_0",
         "remote" : {
           "obs" : {
             "obs_url" : "/test/data/py_minist/"
           }
         }
       } ],
       "outputs" : [ {
         "name" : "train_url",
         "local_dir" : "/home/ma-user/modelarts/outputs/train_url_0",
         "remote" : {
           "obs" : {
             "obs_url" : "/test/train_output/"
           }
         }
       } ],
       "engine" : {
         "engine_id" : "pytorch-cp36-1.4.0-v2",
         "engine_name" : "PyTorch",
         "engine_version" : "PyTorch-1.4.0-python3.6-v2"
       }
     },
     "spec" : {
       "resource" : {
         "flavor_id" : "modelarts.vm.pnt1.large.eco",
         "node_count" : 1,
         "flavor_detail" : {
           "flavor_type" : "GPU",
           "billing" : {
             "code" : "modelarts.vm.gpu.pnt1.eco",
             "unit_num" : 1
           },
           "flavor_info" : {
             "cpu" : {
               "arch" : "x86",
               "core_num" : 8
             },
             "gpu" : {
               "unit_num" : 1,
               "memory" : "8GB"
             },
             "memory" : {
               "size" : 64,
               "unit" : "GB"
             }
           }
         }
       },
       "custom_metrics" : [ {
         "metrics_url" : "/raw_text",
         "metrics_port" : 5006
       } ]
     }
   }

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
200         ok
=========== ===========

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
