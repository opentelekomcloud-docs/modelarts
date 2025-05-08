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

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                              |
   +=================+=================+=================+==========================================================================================+
   | project_id      | Yes             | String          | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   |                 |                 |                 |                                                                                          |
   |                 |                 |                 | Minimum: **32**                                                                          |
   |                 |                 |                 |                                                                                          |
   |                 |                 |                 | Maximum: **36**                                                                          |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------+
   | pool_name       | Yes             | String          | Resource pool to which a job belongs                                                     |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   +------------+------------------------------------------------------------------------------+----------------+
   | Parameter  | Type                                                                         | Description    |
   +============+==============================================================================+================+
   | statistics | :ref:`statistics <en-us_topic_0000002268720673__response_statistics>` object | Job statistics |
   +------------+------------------------------------------------------------------------------+----------------+

.. _en-us_topic_0000002268720673__response_statistics:

.. table:: **Table 3** statistics

   +-----------+--------------------------------------------------------------------------------------------------------+-----------------------------------------+
   | Parameter | Type                                                                                                   | Description                             |
   +===========+========================================================================================================+=========================================+
   | total     | Integer                                                                                                | Number of statistics lists              |
   +-----------+--------------------------------------------------------------------------------------------------------+-----------------------------------------+
   | items     | Array of :ref:`WorkloadStatistics <en-us_topic_0000002268720673__response_workloadstatistics>` objects | Statistics of jobs with a specific type |
   +-----------+--------------------------------------------------------------------------------------------------------+-----------------------------------------+

.. _en-us_topic_0000002268720673__response_workloadstatistics:

.. table:: **Table 4** WorkloadStatistics

   +-----------------------+----------------------------------------------------------------------+--------------------------------------+
   | Parameter             | Type                                                                 | Description                          |
   +=======================+======================================================================+======================================+
   | type                  | String                                                               | Job type. Options:                   |
   |                       |                                                                      |                                      |
   |                       |                                                                      | -  **train**: training job           |
   |                       |                                                                      |                                      |
   |                       |                                                                      | -  **infer**: inference job          |
   |                       |                                                                      |                                      |
   |                       |                                                                      | -  **notebook**: notebook job        |
   +-----------------------+----------------------------------------------------------------------+--------------------------------------+
   | total                 | Integer                                                              | Number of jobs                       |
   +-----------------------+----------------------------------------------------------------------+--------------------------------------+
   | status                | :ref:`status <en-us_topic_0000002268720673__response_status>` object | Number of jobs in different statuses |
   +-----------------------+----------------------------------------------------------------------+--------------------------------------+

.. _en-us_topic_0000002268720673__response_status:

.. table:: **Table 5** status

   =========== ======= ========================================
   Parameter   Type    Description
   =========== ======= ========================================
   Queue       Integer Number of queuing jobs
   Pending     Integer Number of pending jobs
   Abnormal    Integer Number of abnormal jobs
   Terminating Integer Number of jobs that are being terminated
   Creating    Integer Number of jobs that are being created
   Running     Integer Number of running jobs
   Completed   Integer Number of completed jobs
   Terminated  Integer Number of terminated jobs
   Failed      Integer Number of jobs that fail to be executed
   =========== ======= ========================================

**Status code: 400**

.. table:: **Table 6** Response body parameters

   +-----------------------+-----------------------+-----------------------+
   | Parameter             | Type                  | Description           |
   +=======================+=======================+=======================+
   | error_code            | String                | Error code            |
   |                       |                       |                       |
   |                       |                       | Minimum: **8**        |
   |                       |                       |                       |
   |                       |                       | Maximum: **36**       |
   +-----------------------+-----------------------+-----------------------+
   | error_msg             | String                | Error message         |
   |                       |                       |                       |
   |                       |                       | Minimum: **2**        |
   |                       |                       |                       |
   |                       |                       | Maximum: **512**      |
   +-----------------------+-----------------------+-----------------------+

**Status code: 404**

.. table:: **Table 7** Response body parameters

   +-----------------------+-----------------------+-----------------------+
   | Parameter             | Type                  | Description           |
   +=======================+=======================+=======================+
   | error_code            | String                | Error code            |
   |                       |                       |                       |
   |                       |                       | Minimum: **8**        |
   |                       |                       |                       |
   |                       |                       | Maximum: **36**       |
   +-----------------------+-----------------------+-----------------------+
   | error_msg             | String                | Error message         |
   |                       |                       |                       |
   |                       |                       | Minimum: **2**        |
   |                       |                       |                       |
   |                       |                       | Maximum: **512**      |
   +-----------------------+-----------------------+-----------------------+

Example Requests
----------------

None

Example Responses
-----------------

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
