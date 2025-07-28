:original_name: BatchBindPoolNodes.html

.. _BatchBindPoolNodes:

Binding Nodes to a Logical Subpool in Batches
=============================================

Function
--------

This API is used to bind nodes in a logical subpool to another logical subpool when node binding is enabled for a physical dedicated pool.

URI
---

POST /v2/{project_id}/pools/{pool_name}/nodes/batch-bind

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

   +-----------+-----------+-------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type                                                                                      | Description                                                                        |
   +===========+===========+===========================================================================================+====================================================================================+
   | nodes     | Yes       | Array of :ref:`BindNodeItem <en-us_topic_0000002374896585__request_bindnodeitem>` objects | List of nodes to be bound with another pool.                                       |
   +-----------+-----------+-------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------+
   | drain     | No        | Boolean                                                                                   | Whether to drain the node to be bound with another pool. **true**: Drain the node. |
   +-----------+-----------+-------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------+

.. _en-us_topic_0000002374896585__request_bindnodeitem:

.. table:: **Table 3** BindNodeItem

   +-----------+-----------+--------+-------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                       |
   +===========+===========+========+===================================================================================================================+
   | name      | Yes       | String | Name of the node to be bound with another pool.                                                                   |
   +-----------+-----------+--------+-------------------------------------------------------------------------------------------------------------------+
   | quotaName | Yes       | String | ID of the logical subpool bound to the node. If the value is empty, the node is not bound to any logical subpool. |
   +-----------+-----------+--------+-------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

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

Bind nodes to logical subpool pool-a26d-prjid.

.. code-block:: text

   POST /v2/{project_id}/pools/{pool_name}/nodes/batch-bind

   {
     "nodes" : [ {
       "name" : "os-node-created-8888g",
       "quotaName" : "pool-a26d-prjid"
     } ]
   }

Example Responses
-----------------

**Status code: 200**

OK.

.. code-block::

   { }

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
