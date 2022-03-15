Querying the Status of a Dataset Synchronization Task
=====================================================

Function
--------

This API is used to query the status of a dataset synchronization task.

URI
---

GET /v2/{project_id}/datasets/{dataset_id}/sync-data/status

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                                                |
   +============+===========+========+============================================================================================================================================================+
   | dataset_id | Yes       | String | Dataset ID.                                                                                                                                                |
   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see `Obtaining a Project ID <../../common_parameters/obtaining_a_project_id_and_name.html>`__. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**



.. _SyncDataSourceStateresponseSyncDataSourceStatusResp:

.. table:: **Table 2** Response body parameters

   +-----------------------+-----------------------+-----------------------------------------------+
   | Parameter             | Type                  | Description                                   |
   +=======================+=======================+===============================================+
   | add_sample_count      | Long                  | Number of added samples.                      |
   +-----------------------+-----------------------+-----------------------------------------------+
   | create_time           | Long                  | Task creation time.                           |
   +-----------------------+-----------------------+-----------------------------------------------+
   | dataset_id            | String                | Dataset ID.                                   |
   +-----------------------+-----------------------+-----------------------------------------------+
   | deleted_sample_count  | Long                  | Number of deleted samples.                    |
   +-----------------------+-----------------------+-----------------------------------------------+
   | duration_time         | Long                  | Task running time.                            |
   +-----------------------+-----------------------+-----------------------------------------------+
   | error_code            | String                | Error code.                                   |
   +-----------------------+-----------------------+-----------------------------------------------+
   | error_msg             | String                | Error message.                                |
   +-----------------------+-----------------------+-----------------------------------------------+
   | status                | String                | Status of a task. The options are as follows: |
   |                       |                       |                                               |
   |                       |                       | -  **QUEUING**: queuing                       |
   |                       |                       |                                               |
   |                       |                       | -  **STARTING**: execution started            |
   |                       |                       |                                               |
   |                       |                       | -  **RUNNING**: running                       |
   |                       |                       |                                               |
   |                       |                       | -  **COMPLETED**: completed                   |
   |                       |                       |                                               |
   |                       |                       | -  **FAILED**: failed                         |
   |                       |                       |                                               |
   |                       |                       | -  **NOT_EXIST**: not found                   |
   +-----------------------+-----------------------+-----------------------------------------------+
   | task_id               | String                | Synchronization task ID.                      |
   +-----------------------+-----------------------+-----------------------------------------------+
   | total_sample_count    | Long                  | Total number of samples.                      |
   +-----------------------+-----------------------+-----------------------------------------------+

Example Requests
----------------

Obtaining the Status of a Dataset Synchronization

.. code-block::

   GET https://{endpoint}/v2/{project_id}/datasets/{dataset_id}/sync-data/status

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "status" : "COMPLETED",
     "dataset_id" : "gfghHSokody6AJigS5A"
   }

Status Codes
------------



.. _SyncDataSourceStatestatuscode:

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

See `Error Codes <../../common_parameters/error_codes.html>`__.


