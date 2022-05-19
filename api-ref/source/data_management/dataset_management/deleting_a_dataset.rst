:original_name: DeleteDataset.html

.. _DeleteDataset:

Deleting a Dataset
==================

Function
--------

This API is used to delete a dataset without deleting the source data of the dataset.

URI
---

DELETE /v2/{project_id}/datasets/{dataset_id}

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                        |
   +============+===========+========+====================================================================================================================+
   | dataset_id | Yes       | String | Dataset ID.                                                                                                        |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <modelarts_03_0147>`. |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

None

Example Requests
----------------

Deleting a Dataset

.. code-block:: text

   DELETE https://{endpoint}/v2/{project_id}/datasets/{dataset_id}

Example Responses
-----------------

**Status code: 204**

No Content

.. code-block::

   { }

Status Codes
------------

=========== ============
Status Code Description
=========== ============
204         No Content
401         Unauthorized
403         Forbidden
=========== ============

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
