:original_name: ShowWorkloadStatistics.html

.. _ShowWorkloadStatistics:

Obtaining Statistics About Dedicated Resource Pool Jobs
=======================================================

Function
--------

This API is used to obtain statistics about dedicated resource pool jobs.

URI
---

GET /v2/{project_id}/statistics/pools/{pool_name}/workloads

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                            |
   +============+===========+========+========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`.                               |
   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------+
   | pool_name  | Yes       | String | ID of the resource pool to which a job belongs. The value is the **metadata.name** field in the resource pool details. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   +-----------+------------------------------------------------------------------------------------------------------+------------------------------------------+
   | Parameter | Type                                                                                                 | Description                              |
   +===========+======================================================================================================+==========================================+
   | statics   | :ref:`WorkloadListStatistics <en-us_topic_0000002341058322__response_workloadliststatistics>` object | Statistics on jobs in the resource pool. |
   +-----------+------------------------------------------------------------------------------------------------------+------------------------------------------+

.. _en-us_topic_0000002341058322__response_workloadliststatistics:

.. table:: **Table 3** WorkloadListStatistics

   +-----------+--------------------------------------------------------------------------------------------------------+------------------------------------+
   | Parameter | Type                                                                                                   | Description                        |
   +===========+========================================================================================================+====================================+
   | total     | Integer                                                                                                | Number of statistics lists.        |
   +-----------+--------------------------------------------------------------------------------------------------------+------------------------------------+
   | items     | Array of :ref:`WorkloadStatistics <en-us_topic_0000002341058322__response_workloadstatistics>` objects | Statistics of different job types. |
   +-----------+--------------------------------------------------------------------------------------------------------+------------------------------------+

.. _en-us_topic_0000002341058322__response_workloadstatistics:

.. table:: **Table 4** WorkloadStatistics

   +-----------------------+----------------------------------------------------------------------------------------------------------+--------------------------------------+
   | Parameter             | Type                                                                                                     | Description                          |
   +=======================+==========================================================================================================+======================================+
   | type                  | String                                                                                                   | Job type. Options:                   |
   |                       |                                                                                                          |                                      |
   |                       |                                                                                                          | -  **train**: training job           |
   |                       |                                                                                                          |                                      |
   |                       |                                                                                                          | -  **infer**: inference job          |
   |                       |                                                                                                          |                                      |
   |                       |                                                                                                          | -  **notebook**: notebook jobs       |
   +-----------------------+----------------------------------------------------------------------------------------------------------+--------------------------------------+
   | total                 | Integer                                                                                                  | Number of jobs                       |
   +-----------------------+----------------------------------------------------------------------------------------------------------+--------------------------------------+
   | status                | :ref:`WorkloadStatusStatistics <en-us_topic_0000002341058322__response_workloadstatusstatistics>` object | Number of jobs in different statuses |
   +-----------------------+----------------------------------------------------------------------------------------------------------+--------------------------------------+

.. _en-us_topic_0000002341058322__response_workloadstatusstatistics:

.. table:: **Table 5** WorkloadStatusStatistics

   =========== ====== ====================================================
   Parameter   Type   Description
   =========== ====== ====================================================
   Queue       String Number of jobs queued in the resource pool.
   Pending     String Number of jobs being scheduled in the resource pool.
   Abnormal    String Number of abnormal jobs.
   Terminating String Number of jobs that are being terminated.
   Creating    String Number of jobs that are being created.
   Running     String Number of running jobs.
   Completed   String Number of completed jobs.
   Terminated  String Number of terminated jobs.
   Failed      String Number of jobs that fail to be executed.
   =========== ====== ====================================================

**Status code: 400**

.. table:: **Table 6** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   error_code String Error code
   error_msg  String Error message
   ========== ====== =============

**Status code: 404**

.. table:: **Table 7** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   error_code String Error code
   error_msg  String Error message
   ========== ====== =============

Example Requests
----------------

Obtain statistics for resource pool jobs.

.. code-block:: text

   GET https://{endpoint}/v2/{project_id}/statistics/pools/{pool_name}/workloads

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "statistics" : {
       "total" : 234,
       "items" : [ {
         "type" : "train",
         "total" : 234,
         "status" : {
           "Pending" : 0,
           "Queue" : 234,
           "Running" : 0
         }
       } ]
     }
   }

**Status code: 400**

Bad request

.. code-block::

   {
     "error_code" : "ModelArts.50004000",
     "error_msg" : "Bad request."
   }

**Status code: 404**

Not found

.. code-block::

   {
     "error_code" : "ModelArts.50015001",
     "error_msg" : "Pool {name} not found."
   }

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
200         OK
400         Bad request
404         Not found
=========== ===========

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
