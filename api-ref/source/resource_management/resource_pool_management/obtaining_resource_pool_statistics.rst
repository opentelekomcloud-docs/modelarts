:original_name: ShowPoolStatistics.html

.. _ShowPoolStatistics:

Obtaining Resource Pool Statistics
==================================

Function
--------

This API is used to obtain resource pool statistics.

URI
---

GET /v2/{project_id}/statistics/pools

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                              |
   +============+===========+========+==========================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   =========== ========= ====== =========================================
   Parameter   Mandatory Type   Description
   =========== ========= ====== =========================================
   workspaceId No        String Workspace ID. The default value is **0**.
   =========== ========= ====== =========================================

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +---------------+------------------------------------------------------------------------------+--------------------------+
   | Parameter     | Type                                                                         | Description              |
   +===============+==============================================================================+==========================+
   | statistics    | :ref:`statistics <en-us_topic_0000002044058296__response_statistics>` object | Resource pool statistics |
   +---------------+------------------------------------------------------------------------------+--------------------------+
   | operationTime | String                                                                       | Statistics time          |
   +---------------+------------------------------------------------------------------------------+--------------------------+

.. _en-us_topic_0000002044058296__response_statistics:

.. table:: **Table 4** statistics

   +-----------+----------------------------------------------------------------------+-------------------------------------------------------+
   | Parameter | Type                                                                 | Description                                           |
   +===========+======================================================================+=======================================================+
   | status    | :ref:`status <en-us_topic_0000002044058296__response_status>` object | Statistics about resource pools in different statuses |
   +-----------+----------------------------------------------------------------------+-------------------------------------------------------+

.. _en-us_topic_0000002044058296__response_status:

.. table:: **Table 5** status

   +-----------+---------+----------------------------------------------------------------------------------------------------------+
   | Parameter | Type    | Description                                                                                              |
   +===========+=========+==========================================================================================================+
   | creating  | Integer | Number of resource pools that are being created                                                          |
   +-----------+---------+----------------------------------------------------------------------------------------------------------+
   | created   | Integer | Number of created resource pools                                                                         |
   +-----------+---------+----------------------------------------------------------------------------------------------------------+
   | failed    | Integer | Number of resource pools that failed to be created in the last three days. The maximum value is **500**. |
   +-----------+---------+----------------------------------------------------------------------------------------------------------+

**Status code: 500**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Obtain resource pool statistics.

.. code-block:: text

   GET https://{endpoint}/v2/{project_id}/statistics/pools

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "statistics" : {
       "status" : {
         "created" : 9,
         "creating" : 0,
         "deleting" : 1,
         "failed" : 0,
         "pending" : 0
       }
     },
     "operationTime" : "2025-03-27 11:48:55.446172146 +0000 UTC"
   }

**Status code: 500**

Internal error

.. code-block::

   {
     "error_code" : "ModelArts.50005000",
     "error_msg" : "internal error"
   }

Status Codes
------------

=========== ==============
Status Code Description
=========== ==============
200         OK
500         Internal error
=========== ==============

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
