:original_name: ShowOsConfig.html

.. _ShowOsConfig:

Querying OS Configuration Parameters
====================================

Function
--------

Obtain the configuration parameters of the ModelArts OS service, such as the CIDR block and user resource quota.

Debugging
---------

You can debug this API through automatic authentication in or use the SDK sample code generated by API Explorer.

URI
---

GET /v1/{project_id}/os-user-config

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                              |
   +============+===========+========+==========================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   +------------------+------------------+----------------------------------------------------------------------------------------+
   | Parameter        | Type             | Description                                                                            |
   +==================+==================+========================================================================================+
   | networkCidrs     | Array of strings | Network configuration item.                                                            |
   +------------------+------------------+----------------------------------------------------------------------------------------+
   | networkQuota     | Integer          | Specifies the number of networks that a user can create.                               |
   +------------------+------------------+----------------------------------------------------------------------------------------+
   | poolQuota        | Integer          | Specifies the quota for the number of resource pools that can be created by a user.    |
   +------------------+------------------+----------------------------------------------------------------------------------------+
   | pooHighAvailable | Boolean          | Specifies whether HA resource pools can be created in the current environment or site. |
   +------------------+------------------+----------------------------------------------------------------------------------------+

**Status code: 404**

.. table:: **Table 3** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

Example Requests
----------------

None

Example Responses
-----------------

**Status code: 200**

OK.

.. code-block::

   {
     "networkCidrs" : [ "192.168.0.0/24", "172.16.31.0/16" ],
     "networkQuota" : 15,
     "poolQuota" : 15,
     "pooHighAvailable" : true
   }

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
200         OK.
404         Not Found.
=========== ===========

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
