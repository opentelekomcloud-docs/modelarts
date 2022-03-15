Synchronizing a Dataset
=======================

Function
--------

This API is used to synchronize samples and labeling information from the input dataset path to the dataset.

URI
---

POST /v2/{project_id}/datasets/{dataset_id}/sync-data

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

None

Example Requests
----------------

Synchronizing a Dataset

.. code-block::

   POST https://{endpoint}/v2/{project_id}/datasets/{dataset_id}/sync-data

Example Responses
-----------------

None

Status Codes
------------



.. _SyncDataSourcestatuscode:

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


