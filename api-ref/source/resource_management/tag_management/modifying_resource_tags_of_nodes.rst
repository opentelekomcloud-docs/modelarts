:original_name: UpdateNodeTags.html

.. _UpdateNodeTags:

Modifying Resource Tags of Nodes
================================

Function
--------

This API is used to modify resource tags of a specified node.

URI
---

POST /v1/{project_id}/nodes/{node_name}/tags

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                              |
   +============+===========+========+==========================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | node_name  | Yes       | String | Node ID. The value is the **metadata.name** field in the node details.                   |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request body parameters

   +-----------------+-----------------+-------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                    | Description                                                                                                                 |
   +=================+=================+=========================================================================+=============================================================================================================================+
   | action          | Yes             | String                                                                  | Action performed on resource tags. The options are as follows:                                                              |
   |                 |                 |                                                                         |                                                                                                                             |
   |                 |                 |                                                                         | -  **create**: Add a specified resource tag. If the tag key already exists, the **value** field of that tag is overwritten. |
   |                 |                 |                                                                         |                                                                                                                             |
   |                 |                 |                                                                         | -  **delete**: Delete a specified resource tag. A resource tag with the same key and value will be deleted.                 |
   |                 |                 |                                                                         |                                                                                                                             |
   |                 |                 |                                                                         | -  **reset**: Reset the resource tag to a requested value.                                                                  |
   +-----------------+-----------------+-------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | tags            | Yes             | Array of :ref:`Tag <en-us_topic_0000002374856409__request_tag>` objects | Resource tag list. The value can be empty only when the value of **action** is **reset**.                                   |
   +-----------------+-----------------+-------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002374856409__request_tag:

.. table:: **Table 3** Tag

   ========= ========= ====== ===========
   Parameter Mandatory Type   Description
   ========= ========= ====== ===========
   key       Yes       String Tag key
   value     Yes       String Tag value
   ========= ========= ====== ===========

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------+----------------------------------------------------------------+-------------------+
   | Parameter | Type                                                           | Description       |
   +===========+================================================================+===================+
   | tags      | :ref:`Tag <en-us_topic_0000002374856409__response_tag>` object | Resource tag list |
   +-----------+----------------------------------------------------------------+-------------------+

.. _en-us_topic_0000002374856409__response_tag:

.. table:: **Table 5** Tag

   ========= ====== ===========
   Parameter Type   Description
   ========= ====== ===========
   key       String Tag key
   value     String Tag value
   ========= ====== ===========

**Status code: 400**

.. table:: **Table 6** Response body parameters

   ========== ====== ========================
   Parameter  Type   Description
   ========== ====== ========================
   error_code String Error codes of ModelArts
   error_msg  String Error message
   ========== ====== ========================

**Status code: 401**

.. table:: **Table 7** Response body parameters

   ========== ====== ========================
   Parameter  Type   Description
   ========== ====== ========================
   error_code String Error codes of ModelArts
   error_msg  String Error message
   ========== ====== ========================

**Status code: 403**

.. table:: **Table 8** Response body parameters

   ========== ====== ========================
   Parameter  Type   Description
   ========== ====== ========================
   error_code String Error codes of ModelArts
   error_msg  String Error message
   ========== ====== ========================

**Status code: 404**

.. table:: **Table 9** Response body parameters

   ========== ====== ========================
   Parameter  Type   Description
   ========== ====== ========================
   error_code String Error codes of ModelArts
   error_msg  String Error message
   ========== ====== ========================

Example Requests
----------------

-  Delete resource tags from a specified node.

   .. code-block::

      https://{endpoint}/v1/{project_id}/nodes/os-node-created-520ad/tags

      {
        "action" : "delete",
        "tags" : [ {
          "key" : "key1",
          "value" : "value1"
        } ]
      }

-  Add resource tags to a specified node.

   .. code-block::

      https://{endpoint}/v1/{project_id}/nodes/os-node-created-520ad/tags

      {
        "action" : "create",
        "tags" : [ {
          "key" : "key1",
          "value" : "value1"
        } ]
      }

Example Responses
-----------------

**Status code: 200**

Tags added.

.. code-block::

   {
     "tags" : [ {
       "key" : "test",
       "value" : "service-gpu"
     }, {
       "key" : "key1",
       "value" : "value1"
     } ]
   }

Status Codes
------------

=========== ========================
Status Code Description
=========== ========================
200         Tags added.
400         Invalid parameter.
401         Authentication failed.
403         Insufficient permission.
404         Resource not found.
=========== ========================

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
