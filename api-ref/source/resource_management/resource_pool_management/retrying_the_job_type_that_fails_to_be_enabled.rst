:original_name: RetryPoolScope.html

.. _RetryPoolScope:

Retrying the Job Type That Fails to Be Enabled
==============================================

Function
--------

This API is used to retry the job type that fails to be enabled.

URI
---

POST /v2/{project_id}/pools/{pool_name}/retry-scope

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

   ========= ========= ====== =======================
   Parameter Mandatory Type   Description
   ========= ========= ====== =======================
   scope     Yes       String Job type to be retried.
   ========= ========= ====== =======================

Response Parameters
-------------------

**Status code: 400**

.. table:: **Table 3** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Retry the Infer job type.

.. code-block::

   /v2/{project_id}/pools/{pool_name}/retry-scope

   {
     "scope" : "Infer"
   }

Example Responses
-----------------

**Status code: 200**

OK.

.. code-block::

   { }

**Status code: 400**

Bad request.

.. code-block::

   {
     "error_code" : "ModelArts.50004000",
     "error_msg" : "Bad request. The pool pool-dly-op-0c2098ebae80d3e22f31c011e23a97cd scope Train cannot be enabled."
   }

Status Codes
------------

=========== ============
Status Code Description
=========== ============
200         OK.
400         Bad request.
=========== ============

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
