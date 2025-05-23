:original_name: BatchDeletePoolNodes.html

.. _BatchDeletePoolNodes:

Deleting Nodes in Batches
=========================

Function
--------

This API is used to delete nodes from a specified resource pool in batches. At least one node must be reserved in the resource pool.

URI
---

POST /v2/{project_id}/pools/{pool_name}/nodes/batch-delete

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                              |
   +============+===========+========+==========================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | pool_name  | Yes       | String | Name of a resource pool                                                                  |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request body parameters

   +-----------------+-----------+------------------+----------------------------------+
   | Parameter       | Mandatory | Type             | Description                      |
   +=================+===========+==================+==================================+
   | deleteNodeNames | Yes       | Array of strings | Names of the nodes to be deleted |
   +-----------------+-----------+------------------+----------------------------------+

Response Parameters
-------------------

**Status code: 404**

.. table:: **Table 3** Response body parameters

   +-----------------------+-----------------------+-----------------------+
   | Parameter             | Type                  | Description           |
   +=======================+=======================+=======================+
   | error_code            | String                | Error code.           |
   |                       |                       |                       |
   |                       |                       | Minimum: **8**        |
   |                       |                       |                       |
   |                       |                       | Maximum: **36**       |
   +-----------------------+-----------------------+-----------------------+
   | error_msg             | String                | Error message.        |
   |                       |                       |                       |
   |                       |                       | Minimum: **2**        |
   |                       |                       |                       |
   |                       |                       | Maximum: **512**      |
   +-----------------------+-----------------------+-----------------------+

Example Requests
----------------

.. code-block:: text

   POST /v2/{project_id}/pools/{pool_name}/nodes/batch-delete

   {
     "deleteNodeNames" : [ "os-node-created-mnmcf" ]
   }

Example Responses
-----------------

**Status code: 404**

Not found

.. code-block::

   {
     "error_code" : "ModelArts.50015001",
     "error_msg" : "pool not found"
   }

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
200         OK
404         Not found
=========== ===========

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
