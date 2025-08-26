:original_name: ListTrainingJobEvents.html

.. _ListTrainingJobEvents:

Obtaining the Events of a Training Job
======================================

Function
--------

This API is used to obtain the events of a training job.

URI
---

GET /v2/{project_id}/training-jobs/{training_job_id}/events

.. table:: **Table 1** Path Parameters

   +-----------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory | Type   | Description                                                                                                              |
   +=================+===========+========+==========================================================================================================================+
   | project_id      | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`.                                 |
   +-----------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | training_job_id | Yes       | String | Training job ID For details about how to obtain the value, see :ref:`Querying the Training Job List <listtrainingjobs>`. |
   +-----------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +------------+-----------+---------+---------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type    | Description                                                                                                   |
   +============+===========+=========+===============================================================================================================+
   | offset     | No        | Integer | Offset of a data entry.                                                                                       |
   +------------+-----------+---------+---------------------------------------------------------------------------------------------------------------+
   | limit      | No        | Integer | Maximum number of records returned on each page. The value ranges from 1 to 100. The default value is **50**. |
   +------------+-----------+---------+---------------------------------------------------------------------------------------------------------------+
   | order      | No        | String  | instance order                                                                                                |
   +------------+-----------+---------+---------------------------------------------------------------------------------------------------------------+
   | start_time | No        | String  | Start time, which must be passed together with the end time                                                   |
   +------------+-----------+---------+---------------------------------------------------------------------------------------------------------------+
   | end_time   | No        | String  | End time, which must be passed together with the start time                                                   |
   +------------+-----------+---------+---------------------------------------------------------------------------------------------------------------+
   | level      | No        | String  | Level of the event to be returned. The value range is [Info Error Warning].                                   |
   +------------+-----------+---------+---------------------------------------------------------------------------------------------------------------+
   | pattern    | No        | String  | Content contained in the event. The value contains a maximum of 256 characters.                               |
   +------------+-----------+---------+---------------------------------------------------------------------------------------------------------------+
   | source     | No        | String  | Source of the returned event. The value range is [**K8S Job Task**].                                          |
   +------------+-----------+---------+---------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   X-Language No        String Language
   ========== ========= ====== ===========

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +------------+-----------------------------------------------------------------------------------------------------------+--------------------------------------------------+
   | Parameter  | Type                                                                                                      | Description                                      |
   +============+===========================================================================================================+==================================================+
   | total      | String                                                                                                    | Total number of records.                         |
   +------------+-----------------------------------------------------------------------------------------------------------+--------------------------------------------------+
   | limit      | String                                                                                                    | Maximum number of records that can be displayed. |
   +------------+-----------------------------------------------------------------------------------------------------------+--------------------------------------------------+
   | offset     | String                                                                                                    | Start number of records.                         |
   +------------+-----------------------------------------------------------------------------------------------------------+--------------------------------------------------+
   | order      | String                                                                                                    | Sorting order.                                   |
   +------------+-----------------------------------------------------------------------------------------------------------+--------------------------------------------------+
   | start_time | String                                                                                                    | Start time of an event.                          |
   +------------+-----------------------------------------------------------------------------------------------------------+--------------------------------------------------+
   | end_time   | String                                                                                                    | End time of an event.                            |
   +------------+-----------------------------------------------------------------------------------------------------------+--------------------------------------------------+
   | events     | Array of :ref:`Event <en-us_topic_0000002374896653__en-us_topic_0000002055164106_response_event>` objects | Event list.                                      |
   +------------+-----------------------------------------------------------------------------------------------------------+--------------------------------------------------+

.. _en-us_topic_0000002374896653__en-us_topic_0000002055164106_response_event:

.. table:: **Table 5** Event

   ========= ====== ==========================
   Parameter Type   Description
   ========= ====== ==========================
   message   String Event information.
   level     String Event severity.
   time      String Time when an event occurs.
   source    String Event source
   ========= ====== ==========================

**Status code: 400**

.. table:: **Table 6** Response body parameters

   ========== ====== =========================
   Parameter  Type   Description
   ========== ====== =========================
   error_code String Error codes of ModelArts.
   error_msg  String Error message.
   ========== ====== =========================

Example Requests
----------------

.. code-block:: text

   GET https://endpoint/v2/{project_id}/training-jobs/{training_job_id}/events?order=desc&offset=0&limit=10&start_time=1669449696964&end_time=1669711991259

Example Responses
-----------------

**Status code: 200**

ok

.. code-block::

   {
     "total" : 27,
     "limit" : 10,
     "offset" : 0,
     "order" : "desc",
     "start_time" : "2022-11-26T16:01:36+08:00",
     "end_time" : "2022-11-29T16:53:11+08:00",
     "events" : [ {
       "time" : "2022-11-26T16:03:41+08:00",
       "level" : "Error",
       "message" : "Training job failed.",
       "source" : "Job"
     }, {
       "time" : "2022-11-26T16:03:16+08:00",
       "level" : "Info",
       "message" : "[Job: modelarts-job-5bd61eea-9de2-4864-a0f7-5fae966171b5] ExecuteAction: Start to execute action TerminateJob",
       "source" : "K8S"
     }, {
       "time" : "2022-11-26T16:03:12+08:00",
       "level" : "Info",
       "message" : "[worker-0][time used: 0.296s] Upload training output(parameter name: train_url) finished.",
       "source" : "Task"
     }, {
       "time" : "2022-11-26T16:03:12+08:00",
       "level" : "Info",
       "message" : "[worker-0] Training output(parameter name: train_url) Uploading.",
       "source" : "Task"
     }, {
       "time" : "2022-11-26T16:03:11+08:00",
       "level" : "Info",
       "message" : "[worker-0] Training finished. Exit code 1.",
       "source" : "Task"
     }, {
       "time" : "2022-11-26T16:02:10+08:00",
       "level" : "Info",
       "message" : "[worker-0] training started.",
       "source" : "Task"
     }, {
       "time" : "2022-11-26T16:02:09+08:00",
       "level" : "Info",
       "message" : "Training job is running.",
       "source" : "Job"
     }, {
       "time" : "2022-11-26T16:02:06+08:00",
       "level" : "Info",
       "message" : "[Pod: modelarts-job-5bd61eea-9de2-4864-a0f7-5fae966171b5-worker-0] Started: Started container",
       "source" : "K8S"
     }, {
       "time" : "2022-11-26T16:02:06+08:00",
       "level" : "Info",
       "message" : "[Pod: modelarts-job-5bd61eea-9de2-4864-a0f7-5fae966171b5-worker-0] SuccessfulCreate: Created container",
       "source" : "K8S"
     }, {
       "time" : "2022-11-26T16:02:05+08:00",
       "level" : "Info",
       "message" : "[Pod: modelarts-job-5bd61eea-9de2-4864-a0f7-5fae966171b5-worker-0] Pulled: Successfully pulled image \"resource-path/modelarts-job-dev-image/modelarts-tool-container:1.0.0-5.3.1-b002.2\"",
       "source" : "K8s"
     } ]
   }

**Status code: 400**

Bad request.

.. code-block::

   {
     "error_code" : "ModelArts.50004000",
     "error_msg" : "Bad request."
   }

Status Codes
------------

=========== ============
Status Code Description
=========== ============
200         ok
400         Bad request.
=========== ============

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
