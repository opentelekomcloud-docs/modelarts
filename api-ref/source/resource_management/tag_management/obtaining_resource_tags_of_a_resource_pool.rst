:original_name: ShowPoolTags.html

.. _ShowPoolTags:

Obtaining Resource Tags of a Resource Pool
==========================================

Function
--------

This API is used to obtain resource tags of a specified resource pool.

URI
---

GET /v1/{project_id}/pools/{pool_name}/tags

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

None

Response Parameters
-------------------

**Status code: 204**

.. table:: **Table 2** Response body parameters

   +-----------+----------------------------------------------------------------+-------------------+
   | Parameter | Type                                                           | Description       |
   +===========+================================================================+===================+
   | tags      | :ref:`Tag <en-us_topic_0000002340898526__response_tag>` object | Resource tag list |
   +-----------+----------------------------------------------------------------+-------------------+

.. _en-us_topic_0000002340898526__response_tag:

.. table:: **Table 3** Tag

   ========= ====== ===========
   Parameter Type   Description
   ========= ====== ===========
   key       String Tag key
   value     String Tag value
   ========= ====== ===========

**Status code: 400**

.. table:: **Table 4** Response body parameters

   ========== ====== ========================
   Parameter  Type   Description
   ========== ====== ========================
   error_code String Error codes of ModelArts
   error_msg  String Error message
   ========== ====== ========================

**Status code: 401**

.. table:: **Table 5** Response body parameters

   ========== ====== ========================
   Parameter  Type   Description
   ========== ====== ========================
   error_code String Error codes of ModelArts
   error_msg  String Error message
   ========== ====== ========================

**Status code: 403**

.. table:: **Table 6** Response body parameters

   ========== ====== ========================
   Parameter  Type   Description
   ========== ====== ========================
   error_code String Error codes of ModelArts
   error_msg  String Error message
   ========== ====== ========================

**Status code: 404**

.. table:: **Table 7** Response body parameters

   ========== ====== ========================
   Parameter  Type   Description
   ========== ====== ========================
   error_code String Error codes of ModelArts
   error_msg  String Error message
   ========== ====== ========================

Example Requests
----------------

Obtain resource tags of a specified resource pool.

.. code-block::

   https://{endpoint}/v1/{project_id}/pools/{pool_name}/tags

Example Responses
-----------------

**Status code: 204**

Tag list.

.. code-block::

   {
     "tags" : [ {
       "key" : "dev",
       "value" : "dev1"
     } ]
   }

Status Codes
------------

=========== ========================
Status Code Description
=========== ========================
204         Tag list.
400         Invalid parameters.
401         Authentication failed.
403         Insufficient permission.
404         Resource not found.
=========== ========================

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
