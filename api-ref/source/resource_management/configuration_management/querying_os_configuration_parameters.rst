:original_name: ShowOsConfig.html

.. _ShowOsConfig:

Querying OS Configuration Parameters
====================================

Function
--------

This API is used to obtain the configuration parameters of the ModelArts OS service, such as the CIDR block and user resource quota.

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

   +--------------------+------------------+---------------------------------------------------------------------------------------------------+
   | Parameter          | Type             | Description                                                                                       |
   +====================+==================+===================================================================================================+
   | networkCidrs       | Array of strings | Network parameters                                                                                |
   +--------------------+------------------+---------------------------------------------------------------------------------------------------+
   | networkQuota       | Integer          | Network quota                                                                                     |
   +--------------------+------------------+---------------------------------------------------------------------------------------------------+
   | poolQuota          | Integer          | Resource pool quota                                                                               |
   +--------------------+------------------+---------------------------------------------------------------------------------------------------+
   | pooHighAvailable   | Boolean          | Whether resource pools with high availability can be created in the current environment or region |
   +--------------------+------------------+---------------------------------------------------------------------------------------------------+
   | maxPoolFlavors     | Integer          | Maximum number of resource flavors supported by a resource pool                                   |
   +--------------------+------------------+---------------------------------------------------------------------------------------------------+
   | clusterFlavorSpecs | String           | Specifications of management nodes in the Kubernetes cluster                                      |
   +--------------------+------------------+---------------------------------------------------------------------------------------------------+

**Status code: 404**

.. table:: **Table 3** Response body parameters

   +-----------------------+-----------------------+-----------------------+
   | Parameter             | Type                  | Description           |
   +=======================+=======================+=======================+
   | error_code            | String                | Error code            |
   |                       |                       |                       |
   |                       |                       | Minimum: **8**        |
   |                       |                       |                       |
   |                       |                       | Maximum: **36**       |
   +-----------------------+-----------------------+-----------------------+
   | error_msg             | String                | Error message         |
   |                       |                       |                       |
   |                       |                       | Minimum: **2**        |
   |                       |                       |                       |
   |                       |                       | Maximum: **512**      |
   +-----------------------+-----------------------+-----------------------+

Example Requests
----------------

None

Example Responses
-----------------

**Status code: 200**

OK

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
200         OK
404         Not found
=========== ===========

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
