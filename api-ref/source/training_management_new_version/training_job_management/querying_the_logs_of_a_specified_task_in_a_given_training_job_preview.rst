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

   +-----------------+-----------+--------+---------------------------------------------------------------------------------+
   | Parameter       | Mandatory | Type   | Description                                                                     |
   +=================+===========+========+=================================================================================+
   | project_id      | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID <modelarts_03_0147>`. |
   +-----------------+-----------+--------+---------------------------------------------------------------------------------+
   | training_job_id | Yes       | String | ID of a training job.                                                           |
   +-----------------+-----------+--------+---------------------------------------------------------------------------------+
   | task_id         | Yes       | String | Name of a training job.                                                         |
   +-----------------+-----------+--------+---------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   +--------------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Type    | Description                                                                                                                                                                |
   +==============+=========+============================================================================================================================================================================+
   | content      | String  | Logs. If the size of a log file does not exceed the upper limit (n MB), complete log content will be returned. Otherwise, the latest log content in n MB will be returned. |
   +--------------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | current_size | Integer | Size of the returned log content, in bytes. The maximum size is 5 MB.                                                                                                      |
   +--------------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | full_size    | Integer | Size of complete log content, in bytes                                                                                                                                     |
   +--------------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

The following shows how to query the **work-0** tasks of the training job whose UUID is **2cd88daa-31a4-40a8-a58f-d186b0e93e4f**.

.. code-block:: text

   GET   https://endpoint/v2/{project_id}/training-jobs/2cd88daa-31a4-40a8-a58f-d186b0e93e4f/tasks/worker-0/logs/preview

Example Responses
-----------------

**Status code: 200**

ok

.. code-block::

   {
     "content" : "[Modelarts Service Log]collect and upload ascend logs end at 2021-05-18-14:28:13[Modelarts Service Log]exiting...[Modelarts Service Log]exiting...[Modelarts Service Log]exit with 0[Modelarts Service Log]exit with 0[ModelArts Service Log][INFO][2021/05/18 14:28:14,207]: output-handler finalizing due to: [training finished][ModelArts Service Log][INFO][2021/05/18 14:28:14,207]: output-handler finalized[Modelarts Service Log][sidecar] exiting at 2021-05-18-14:28:14[Modelarts Service Log][sidecar] wait python processes exit...[Modelarts Service Log][sidecar] exit with 0",
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
