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

   +-----------------------+--------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                             | Description                                                                                                         |
   +=======================+==================================================================================================+=====================================================================================================================+
   | networkCidrs          | Array of strings                                                                                 | Network parameters                                                                                                  |
   +-----------------------+--------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | networkQuota          | Integer                                                                                          | Network quota                                                                                                       |
   +-----------------------+--------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | networkSubnetTypes    | Array of strings                                                                                 | List of available network subnet types.                                                                             |
   +-----------------------+--------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | poolQuota             | Integer                                                                                          | Resource pool quota                                                                                                 |
   +-----------------------+--------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | pooHighAvailable      | Boolean                                                                                          | Whether resource pools with high availability can be created in the current environment or region                   |
   +-----------------------+--------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | maxPoolFlavors        | Integer                                                                                          | Maximum number of resource flavors supported by a resource pool                                                     |
   +-----------------------+--------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | clusterFlavorSpecs    | String                                                                                           | Specifications of management nodes in the Kubernetes cluster                                                        |
   +-----------------------+--------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | licenseScopeType      | String                                                                                           | Type of jobs that can be created using the license imported to the current environment. The options are as follows: |
   |                       |                                                                                                  |                                                                                                                     |
   |                       |                                                                                                  | -  **single**: Resource pools that support only training or inference can be created.                               |
   |                       |                                                                                                  |                                                                                                                     |
   |                       |                                                                                                  | -  **multi**: Resource pools that support both training and inference can be created.                               |
   +-----------------------+--------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | nodeOSVersionSupport  | Array of :ref:`OsVersion <en-us_topic_0000002341058338__response_osversion>` objects             | List of available node image versions.                                                                              |
   +-----------------------+--------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | volumeTypes           | Array of strings                                                                                 | Supported disk types.                                                                                               |
   +-----------------------+--------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | poolScopePlugins      | Array of :ref:`PoolScopePlugin <en-us_topic_0000002341058338__response_poolscopeplugin>` objects | Configurations of the resource pool job types.                                                                      |
   +-----------------------+--------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002341058338__response_osversion:

.. table:: **Table 3** OsVersion

   ============ ====== ============================================
   Parameter    Type   Description
   ============ ====== ============================================
   name         String Name of the system image.
   endOfService String Expiration time of the system image service.
   ============ ====== ============================================

.. _en-us_topic_0000002341058338__response_poolscopeplugin:

.. table:: **Table 4** PoolScopePlugin

   +-----------------------+-----------------------+------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                      |
   +=======================+=======================+==================================================================+
   | scope                 | String                | Job type. Options:                                               |
   |                       |                       |                                                                  |
   |                       |                       | -  **Train**: training jobs                                      |
   |                       |                       |                                                                  |
   |                       |                       | -  **Infer**: inference jobs                                     |
   |                       |                       |                                                                  |
   |                       |                       | -  **Notebook**: notebook jobs                                   |
   +-----------------------+-----------------------+------------------------------------------------------------------+
   | plugins               | Array of strings      | Plug-in list.                                                    |
   +-----------------------+-----------------------+------------------------------------------------------------------+
   | externalDependency    | Boolean               | Whether external dependencies exist. The options are as follows: |
   |                       |                       |                                                                  |
   |                       |                       | -  **false**: The job type has no external dependency.           |
   |                       |                       |                                                                  |
   |                       |                       | -  **true**: The job type has external dependencies.             |
   +-----------------------+-----------------------+------------------------------------------------------------------+
   | reservedNetworkCidr   | Array of strings      | Reserved CIDR block.                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------+

**Status code: 404**

.. table:: **Table 5** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   error_code String Error code
   error_msg  String Error message
   ========== ====== =============

Example Requests
----------------

Obtain configuration parameters.

.. code-block:: text

   GET https://{endpoint}/v1/{project_id}/os-user-config

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "clusterFlavorSpecs" : [ "cce.s1.small", "cce.s1.medium", "cce.s2.small", "cce.s2.medium", "cce.s2.large", "cce.s2.xlarge" ],
     "licenseScopeType" : "multi",
     "maxPoolFlavors" : 10,
     "networkCidrs" : [ "192.168.128.0/17", "172.18.0.0/16" ],
     "networkQuota" : 15,
     "networkSubnetTypes" : [ "", "clouddcn" ],
     "nodeOSVersionSupport" : [ {
       "name" : "EulerOS 2.1",
       "endOfService" : "2019-12-31"
     }, {
       "name" : "EulerOS 2.2",
       "endOfService" : "2021-12-31"
     }, {
       "name" : "EulerOS 2.3",
       "endOfService" : "2022-12-31"
     }, {
       "name" : "EulerOS 2.5",
       "endOfService" : "2024-12-31"
     }, {
       "name" : "EulerOS 2.8",
       "endOfService" : "2024-12-31"
     }, {
       "name" : "EulerOS 2.9",
       "endOfService" : "2025-12-31"
     }, {
       "name" : "EulerOS 2.10",
       "endOfService" : "2026-12-31"
     } ],
     "poolHighAvailable" : false,
     "poolQuota" : 15,
     "poolScopePlugins" : [ {
       "scope" : "Train",
       "plugins" : [ "volcano" ]
     }, {
       "scope" : "Infer",
       "plugins" : [ "volcano" ],
       "reservedNetworkCidr" : [ "192.168.0.0/16", "172.16.0.0/16", "10.247.0.0/16" ],
       "externalDependency" : true,
       "supportRetry" : true
     }, {
       "scope" : "Notebook",
       "externalDependency" : true,
       "supportRetry" : true
     } ],
     "volumeTypes" : [ "SSD", "GPSSD", "SAS" ]
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
