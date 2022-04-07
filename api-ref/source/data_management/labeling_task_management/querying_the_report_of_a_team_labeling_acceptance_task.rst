.. _GetWorkforceSamplingTask:

Querying the Report of a Team Labeling Acceptance Task
======================================================

Function
--------

This API is used to query the report of a team labeling acceptance task.

URI
---

GET /v2/{project_id}/datasets/{dataset_id}/workforce-tasks/{workforce_task_id}/acceptance/report

.. table:: **Table 1** Path parameters

   +-------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory | Type   | Description                                                                                                        |
   +===================+===========+========+====================================================================================================================+
   | dataset_id        | Yes       | String | Dataset ID.                                                                                                        |
   +-------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | project_id        | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <modelarts_03_0147>`. |
   +-------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | workforce_task_id | Yes       | String | ID of a team labeling task.                                                                                        |
   +-------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   ================ ========= ====== =====================================
   Parameter        Mandatory Type   Description
   ================ ========= ====== =====================================
   checking_task_id Yes       String ID of the task that is being checked.
   ================ ========= ====== =====================================

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +----------------+----------------------------------------------------------------------------------+----------------------------------+
   | Parameter      | Type                                                                             | Description                      |
   +================+==================================================================================+==================================+
   | checking_stats | :ref:`CheckTaskStats <getworkforcesamplingtask__response_checktaskstats>` object | Real-time acceptance statistics. |
   +----------------+----------------------------------------------------------------------------------+----------------------------------+
   | total_stats    | :ref:`CheckTaskStats <getworkforcesamplingtask__response_checktaskstats>` object | Historical statistics.           |
   +----------------+----------------------------------------------------------------------------------+----------------------------------+

.. _getworkforcesamplingtask__response_checktaskstats:

.. table:: **Table 4** CheckTaskStats

   ====================== ======= ====================================
   Parameter              Type    Description
   ====================== ======= ====================================
   accepted_sample_count  Integer Accepted samples.
   checked_sample_count   Integer Checked samples.
   pass_rate              Double  Pass rate of samples.
   rejected_sample_count  Integer Rejected samples.
   sampled_sample_count   Integer Number of sampled samples.
   sampling_num           Integer Samples of an acceptance task.
   sampling_rate          Double  Sampling rate of an acceptance task.
   score                  String  Acceptance score.
   task_id                String  ID of an acceptance task.
   total_sample_count     Integer Total samples.
   total_score            Long    Total acceptance score.
   unchecked_sample_count Integer Unchecked samples.
   ====================== ======= ====================================

Example Requests
----------------

Querying the Report of a Team Labeling Acceptance Task

.. code-block::

   GET https://{endpoint}/v2/{project_id}/datasets/{dataset_id}/workforce-tasks/{workforce_task_id}/acceptance/report

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "total_stats" : {
       "sampling_rate" : 1.0,
       "sampling_num" : 3,
       "pass_rate" : 0.0,
       "score" : "E",
       "total_score" : 0,
       "total_sample_count" : 3,
       "sampled_sample_count" : 3,
       "unchecked_sample_count" : 3,
       "checked_sample_count" : 0,
       "accepted_sample_count" : 0,
       "rejected_sample_count" : 0
     }
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
