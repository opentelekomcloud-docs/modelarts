:original_name: BatchUpdatePoolNodes.html

.. _BatchUpdatePoolNodes:

Updating Nodes in Batches
=========================

Function
--------

This API is used to update nodes in batches.

URI
---

POST /v2/{project_id}/pools/{pool_name}/nodes/batch-update

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                              |
   +============+===========+========+==========================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | pool_name  | Yes       | String | Resource pool ID. The value is the **metadata.name** field in the resource pool details. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request body parameters

   +-----------------+-----------------+------------------+-------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                       |
   +=================+=================+==================+===================================================================+
   | nodeNames       | Yes             | Array of strings | List of node names to be updated.                                 |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------+
   | action          | Yes             | String           | Action performed for updating a node. The options are as follows: |
   |                 |                 |                  |                                                                   |
   |                 |                 |                  | -  **openHaRedundant**: Enable HA redundancy.                     |
   |                 |                 |                  |                                                                   |
   |                 |                 |                  | -  **closeHaRedundant**: Disable HA redundancy.                   |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +------------------+------------------+-----------------------------------------------+
   | Parameter        | Type             | Description                                   |
   +==================+==================+===============================================+
   | successNodeNames | Array of strings | Names of nodes that are successfully updated. |
   +------------------+------------------+-----------------------------------------------+
   | failNodeNames    | Array of strings | Names of nodes that fail to be updated.       |
   +------------------+------------------+-----------------------------------------------+

**Status code: 404**

.. table:: **Table 4** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Enable node HA redundancy.

.. code-block:: text

   POST /v2/{project_id}/pools/{pool_name}/nodes/batch-update

   {
     "nodeNames" : [ "os-node-created-xzz78" ],
     "action" : "openHaRedundant"
   }

Example Responses
-----------------

**Status code: 200**

OK.

.. code-block::

   {
     "nodes" : [ {
       "name" : "os-node-created-xzz78",
       "status" : "success"
     } ]
   }

**Status code: 404**

Not found.

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
200         OK.
404         Not found.
=========== ===========

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
