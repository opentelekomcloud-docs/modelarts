:original_name: ShowTrainingJobLogsPreview.html

.. _ShowTrainingJobLogsPreview:

Querying the Logs of a Specified Task in a Given Training Job (Preview)
=======================================================================

Function
--------

This API is used to query the logs of a specified task in a given training job (preview).

URI
---

GET /v2/{project_id}/training-jobs/{training_job_id}/tasks/{task_id}/logs/preview

.. table:: **Table 1** Path Parameters

   +-----------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory | Type   | Description                                                                                                              |
   +=================+===========+========+==========================================================================================================================+
   | project_id      | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`.                                 |
   +-----------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | training_job_id | Yes       | String | Training job ID For details about how to obtain the value, see :ref:`Querying the Training Job List <listtrainingjobs>`. |
   +-----------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | task_id         | Yes       | String | Name of a training job. You can obtain the value from the **status.tasks** field in the training job details.            |
   +-----------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | project_id      | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`.                                 |
   +-----------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | training_job_id | Yes       | String | Training job ID For details about how to obtain the value, see :ref:`Querying the Training Job List <listtrainingjobs>`. |
   +-----------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | task_id         | Yes       | String | Name of a training job. You can obtain the value from the **status.tasks** field in the training job details.            |
   +-----------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   +--------------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Type    | Description                                                                                                                                                                                                                                                     |
   +==============+=========+=================================================================================================================================================================================================================================================================+
   | content      | String  | Log content. If the size of a log file does not exceed the upper limit (n MB), all the log files are returned. Otherwise, the latest log file (n MB) is returned. After 2022/03/01 00:00:00 (GMT+08:00), the parameter name is changed from context to content. |
   +--------------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | current_size | Integer | Size of the returned log content, in bytes. The maximum size is 5 MB.                                                                                                                                                                                           |
   +--------------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | full_size    | Integer | Size of complete log content, in bytes                                                                                                                                                                                                                          |
   +--------------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

The following shows how to obtain the worker-0 logs of the training job whose UUID is **2cd88daa-31a4-40a8-a58f-d186b0e93e4f**.

.. code-block:: text

   GET https://endpoint/v2/{project_id}/training-jobs/2cd88daa-31a4-40a8-a58f-d186b0e93e4f/tasks/worker-0/logs/preview

Example Responses
-----------------

**Status code: 200**

ok

.. code-block::

   {
     "content" : "[Modelarts Service Log]collect and upload logs end at 2021-05-18-14:28:13\n[Modelarts Service Log]exiting..:\n [Modelarts Service Log]exiting...\n[Modelarts Service Log]exiting..:\n [Modelarts Service Log]exiting...\n[Modelarts Service Log]exit with :\n [Modelarts Service Log]exit with 0\n[Modelarts Service Log]exit with :\n [Modelarts Service Log]exit with 0\n[ModelArts Service Log][INFO][2021/05/18 14:28:14,207]:\n  output-handler finalizing due to: [training finished]\n[ModelArts Service Log][INFO][2021/05/18 14:28:14,207]:\n  output-handler finalized\n[Modelarts Service Log][sidecar] exiting at 2021-05-18-14:28:14\n[Modelarts Service Log][sidecar] wait python processes exit..:\n  [Modelarts Service Log][sidecar] wait python processes exit...\n[Modelarts Service Log][sidecar] exit with :\n  [Modelarts Service Log][sidecar] exit with 0",
     "current_size" : 126548,
     "full_size" : 5242880
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
