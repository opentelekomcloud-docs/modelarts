Deleting a Dataset Labeling Version
===================================

Function
--------

This API is used to delete a dataset labeling version.

URI
---

DELETE /v2/{project_id}/datasets/{dataset_id}/versions/{version_id}

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                                                |
   +============+===========+========+============================================================================================================================================================+
   | dataset_id | Yes       | String | Dataset ID.                                                                                                                                                |
   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see `Obtaining a Project ID <../../common_parameters/obtaining_a_project_id_and_name.html>`__. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version_id | Yes       | String | Dataset version ID.                                                                                                                                        |
   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

None

Example Requests
----------------

Deleting a Dataset Labeling Version

.. code-block::

   DELETE https://{endpoint}/v2/{project_id}/datasets/{dataset_id}/versions/{version_id}

Example Responses
-----------------

**Status code: 204**

No Content

.. code-block::

   { }

Status Codes
------------



.. _DeleteDatasetVersionstatuscode:

=========== ============
Status Code Description
=========== ============
204         No Content
401         Unauthorized
403         Forbidden
=========== ============

Error Codes
-----------

See `Error Codes <../../common_parameters/error_codes.html>`__.

