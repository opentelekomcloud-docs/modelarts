:original_name: BatchDeletePoolTags.html

.. _BatchDeletePoolTags:

Deleting Resource Pool Tags in Batches
======================================

Function
--------

This API is used to delete tags of a specified resource. Batch deletion is supported.

URI
---

DELETE /v1/{project_id}/pools/{pool_name}/tags/delete

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                 |
   +============+===========+========+=============================================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`.                    |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+
   | pool_name  | Yes       | String | Resource pool name. The value is the **name** value in the **metadata** field of the resource pool details. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request body parameters

   +-----------+-----------+---------------------------------------------------------------------------+--------------------+
   | Parameter | Mandatory | Type                                                                      | Description        |
   +===========+===========+===========================================================================+====================+
   | tags      | Yes       | Array of :ref:`tags <en-us_topic_0000002268800601__request_tags>` objects | Tags to be deleted |
   +-----------+-----------+---------------------------------------------------------------------------+--------------------+

.. _en-us_topic_0000002268800601__request_tags:

.. table:: **Table 3** tags

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                      |
   +=================+=================+=================+==================================================================================================================+
   | key             | Yes             | String          | Tag key                                                                                                          |
   |                 |                 |                 |                                                                                                                  |
   |                 |                 |                 | Minimum: **1**                                                                                                   |
   |                 |                 |                 |                                                                                                                  |
   |                 |                 |                 | Maximum: **128**                                                                                                 |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------+
   | value           | No              | String          | Tag value. This parameter is optional. If this parameter is left blank, the tag that matches the key is deleted. |
   |                 |                 |                 |                                                                                                                  |
   |                 |                 |                 | Minimum: **0**                                                                                                   |
   |                 |                 |                 |                                                                                                                  |
   |                 |                 |                 | Maximum: **255**                                                                                                 |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 204**

.. table:: **Table 4** Response body parameters

   +-----------+----------------------------------------------------------------+-------------------+
   | Parameter | Type                                                           | Description       |
   +===========+================================================================+===================+
   | tags      | :ref:`Tag <en-us_topic_0000002268800601__response_tag>` object | Resource tag list |
   +-----------+----------------------------------------------------------------+-------------------+

.. _en-us_topic_0000002268800601__response_tag:

.. table:: **Table 5** Tag

   +-----------------------+-----------------------+-----------------------+
   | Parameter             | Type                  | Description           |
   +=======================+=======================+=======================+
   | key                   | String                | Tag key               |
   |                       |                       |                       |
   |                       |                       | Minimum: **1**        |
   |                       |                       |                       |
   |                       |                       | Maximum: **128**      |
   +-----------------------+-----------------------+-----------------------+
   | value                 | String                | Tag value             |
   |                       |                       |                       |
   |                       |                       | Minimum: **0**        |
   |                       |                       |                       |
   |                       |                       | Maximum: **255**      |
   +-----------------------+-----------------------+-----------------------+

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

.. code-block::

   https://{endpoint}/v1/{project_id}/pools/a55eba18-1ebf-4e9a-8229-d2d3b593a3dc/tags/delete

   {
     "tags" : [ {
       "key" : "dev",
       "value" : "dev1"
     } ]
   }

Example Responses
-----------------

**Status code: 204**

Tags deleted successfully.

.. code-block::

   {
     "tags" : [ {
       "key" : "dev",
       "value" : "dev1"
     } ]
   }

Status Codes
------------

=========== ==========================
Status Code Description
=========== ==========================
204         Tags deleted successfully.
400         Invalid parameters.
401         Authentication failed.
403         Insufficient permission.
404         Resource not found.
=========== ==========================

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
