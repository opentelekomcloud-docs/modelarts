:original_name: ShowObsUrlOfTrainingJobLogs.html

.. _ShowObsUrlOfTrainingJobLogs:

Querying the Logs of a Specified Task in a Training Job (OBS Link)
==================================================================

Function
--------

This API is used to obtain the logs of a specified task of a training job (temporary OBS link, which is valid for 5 minutes). You can view all logs or download the logs.

URI
---

GET /v2/{project_id}/training-jobs/{training_job_id}/tasks/{task_id}/logs/url

.. table:: **Table 1** Path Parameters

   +-----------------+-----------+--------+---------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory | Type   | Description                                                                                                   |
   +=================+===========+========+===============================================================================================================+
   | project_id      | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`.                      |
   +-----------------+-----------+--------+---------------------------------------------------------------------------------------------------------------+
   | training_job_id | Yes       | String | ID of a training job.                                                                                         |
   +-----------------+-----------+--------+---------------------------------------------------------------------------------------------------------------+
   | task_id         | Yes       | String | Name of a training job. You can obtain the value from the **status.tasks** field in the training job details. |
   +-----------------+-----------+--------+---------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                                               |
   +==============+===========+========+===========================================================================================================================================================================================+
   | Content-Type | No        | String | Message body type. If this parameter is set to text/plain, the temporary preview link is returned. Set this parameter to application/octet-stream. A temporary download link is returned. |
   +--------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------+--------+---------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                       |
   +===========+========+===================================================================================================+
   | obs_url   | String | Temporary OBS URL of logs. You can copy the URL to the browser to view the current complete logs. |
   +-----------+--------+---------------------------------------------------------------------------------------------------+

Example Requests
----------------

The following shows how to query the temporary OBS URL for the **work-0** tasks of the training job whose UUID is **2cd88daa-31a4-40a8-a58f-d186b0e93e4f**.

.. code-block:: text

   GET https://endpoint/v2/{project_id}/training-jobs/2cd88daa-31a4-40a8-a58f-d186b0e93e4f/tasks/worker-0/logs/url?Content-Type=text/plain

Example Responses
-----------------

**Status code: 200**

ok

.. code-block::

   {
     "obs_url" : "http://10.155.101.248:20000/xxxxxx-test/xk/00chess_test/test11/logs/modelarts-job-0f2ccdbb-4f34-4d53-afb9-d526f3be8c68-ma-platform-init-worker-0-172.16.24.51-01909681.log?AWSAccessKeyId=xxxxx"
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
