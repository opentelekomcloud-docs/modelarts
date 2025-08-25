:original_name: ListPoolTags.html

.. _ListPoolTags:

Obtaining All Resource Tags of a Resource Pool
==============================================

Function
--------

This API is used to query all tags of a resource pool in the current project. By default, all workspaces are queried. Tag data is not returned for workspaces on which the user does not have permission.

URI
---

GET /v1/{project_id}/pools/tags

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                              |
   +============+===========+========+==========================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------+-----------+---------+--------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                                                    |
   +===========+===========+=========+================================================================================+
   | limit     | No        | Integer | Maximum number of records returned on each page. The default value is **200**. |
   +-----------+-----------+---------+--------------------------------------------------------------------------------+
   | offset    | No        | Integer | Start page for pagination display. The default value is **0**.                 |
   +-----------+-----------+---------+--------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------+----------------------------------------------------------------+-------------------+
   | Parameter | Type                                                           | Description       |
   +===========+================================================================+===================+
   | tags      | :ref:`Tag <en-us_topic_0000002374856377__response_tag>` object | Resource tag list |
   +-----------+----------------------------------------------------------------+-------------------+

.. _en-us_topic_0000002374856377__response_tag:

.. table:: **Table 4** Tag

   ========= ====== ===========
   Parameter Type   Description
   ========= ====== ===========
   key       String Tag key
   value     String Tag value
   ========= ====== ===========

**Status code: 400**

.. table:: **Table 5** Response body parameters

   ========== ====== ========================
   Parameter  Type   Description
   ========== ====== ========================
   error_code String Error codes of ModelArts
   error_msg  String Error message
   ========== ====== ========================

**Status code: 401**

.. table:: **Table 6** Response body parameters

   ========== ====== ========================
   Parameter  Type   Description
   ========== ====== ========================
   error_code String Error codes of ModelArts
   error_msg  String Error message
   ========== ====== ========================

**Status code: 403**

.. table:: **Table 7** Response body parameters

   ========== ====== ========================
   Parameter  Type   Description
   ========== ====== ========================
   error_code String Error codes of ModelArts
   error_msg  String Error message
   ========== ====== ========================

Example Requests
----------------

.. code-block::

   https://{endpoint}/v1/{project_id}/pools/tags

Example Responses
-----------------

**Status code: 200**

Querying all tags of a specified resource type in a project

.. code-block::

   {
     "tags" : [ {
       "key" : "model_version",
       "values" : [ "0.1", "0.2" ]
     }, {
       "key" : "conda_version",
       "values" : [ "10.2", "11.0" ]
     } ]
   }

Status Codes
------------

=========== ===========================================================
Status Code Description
=========== ===========================================================
200         Querying all tags of a specified resource type in a project
400         Invalid parameter.
401         Authentication failed.
403         Insufficient permission.
=========== ===========================================================

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
