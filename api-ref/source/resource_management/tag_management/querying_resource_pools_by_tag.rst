:original_name: ListPoolsByTags.html

.. _ListPoolsByTags:

Querying Resource Pools by Tag
==============================

Function
--------

This API is used to query resources by tag. Multiple tags can be ANDed. Fuzzy search by resource name is supported.

URI
---

POST /v1/{project_id}/pools/resource-instances/filter

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                              |
   +============+===========+========+==========================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                               |
   +=================+=================+=================+===========================================================================================+
   | limit           | No              | Integer         | Maximum number of records returned on each page. The value ranges from **1** to **1000**. |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | Minimum: **1**                                                                            |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | Maximum: **1000**                                                                         |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | Default: **1000**                                                                         |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+
   | offset          | No              | Integer         | Start page for pagination display. The default value is **0**.                            |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | Minimum: **0**                                                                            |
   |                 |                 |                 |                                                                                           |
   |                 |                 |                 | Default: **0**                                                                            |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   ============ ========= ====== ============
   Parameter    Mandatory Type   Description
   ============ ========= ====== ============
   Content-Type No        String Content-Type
   X-Auth-Token Yes       String User token
   ============ ========= ====== ============

.. table:: **Table 4** Request body parameters

   +-----------+-----------+---------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type                                                                                  | Description                                                                                           |
   +===========+===========+=======================================================================================+=======================================================================================================+
   | tags      | No        | Array of :ref:`CombineTag <en-us_topic_0000002233881258__request_combinetag>` objects | Tags. Only multiple tags can be ANDed. If this parameter is not specified, all resources are queried. |
   +-----------+-----------+---------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | matches   | No        | Array of :ref:`matches <en-us_topic_0000002233881258__request_matches>` objects       | Matching item. Currently, only fuzzy match of resource names is supported.                            |
   +-----------+-----------+---------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002233881258__request_combinetag:

.. table:: **Table 5** CombineTag

   +-----------------+-----------------+------------------+-------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                         |
   +=================+=================+==================+=====================================+
   | key             | Yes             | String           | Tag key                             |
   |                 |                 |                  |                                     |
   |                 |                 |                  | Minimum: **1**                      |
   |                 |                 |                  |                                     |
   |                 |                 |                  | Maximum: **128**                    |
   +-----------------+-----------------+------------------+-------------------------------------+
   | values          | Yes             | Array of strings | Merged tag values with the same key |
   |                 |                 |                  |                                     |
   |                 |                 |                  | Array Length: **0 - 200**           |
   +-----------------+-----------------+------------------+-------------------------------------+

.. _en-us_topic_0000002233881258__request_matches:

.. table:: **Table 6** matches

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                      |
   +=================+=================+=================+==================================================================================================================================+
   | key             | Yes             | String          | Name of the matching item. The options are as follows:                                                                           |
   |                 |                 |                 |                                                                                                                                  |
   |                 |                 |                 | -  **resource_name**                                                                                                             |
   |                 |                 |                 |                                                                                                                                  |
   |                 |                 |                 | Minimum: **1**                                                                                                                   |
   |                 |                 |                 |                                                                                                                                  |
   |                 |                 |                 | Maximum: **128**                                                                                                                 |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------+
   | value           | Yes             | String          | Value of the matching item, no matter whether it is large or small. If **key** is set to **resource_name**, fuzzy match is used. |
   |                 |                 |                 |                                                                                                                                  |
   |                 |                 |                 | Minimum: **0**                                                                                                                   |
   |                 |                 |                 |                                                                                                                                  |
   |                 |                 |                 | Maximum: **255**                                                                                                                 |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 7** Response body parameters

   +-------------+--------------------------------------------------------------------------------------+---------------------------+
   | Parameter   | Type                                                                                 | Description               |
   +=============+======================================================================================+===========================+
   | total_count | Integer                                                                              | Total number of resources |
   +-------------+--------------------------------------------------------------------------------------+---------------------------+
   | resources   | Array of :ref:`resources <en-us_topic_0000002233881258__response_resources>` objects | Resource list             |
   +-------------+--------------------------------------------------------------------------------------+---------------------------+

.. _en-us_topic_0000002233881258__response_resources:

.. table:: **Table 8** resources

   +---------------+--------------------------------------------------------------------------+----------------------------------+
   | Parameter     | Type                                                                     | Description                      |
   +===============+==========================================================================+==================================+
   | resource_name | String                                                                   | Resource name                    |
   +---------------+--------------------------------------------------------------------------+----------------------------------+
   | resource_id   | String                                                                   | Resource ID                      |
   +---------------+--------------------------------------------------------------------------+----------------------------------+
   | tags          | Array of :ref:`Tag <en-us_topic_0000002233881258__response_tag>` objects | All tags of the current resource |
   +---------------+--------------------------------------------------------------------------+----------------------------------+

.. _en-us_topic_0000002233881258__response_tag:

.. table:: **Table 9** Tag

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

.. table:: **Table 10** Response body parameters

   ========== ====== ========================
   Parameter  Type   Description
   ========== ====== ========================
   error_code String Error codes of ModelArts
   error_msg  String Error message
   ========== ====== ========================

**Status code: 401**

.. table:: **Table 11** Response body parameters

   ========== ====== ========================
   Parameter  Type   Description
   ========== ====== ========================
   error_code String Error codes of ModelArts
   error_msg  String Error message
   ========== ====== ========================

**Status code: 403**

.. table:: **Table 12** Response body parameters

   ========== ====== ========================
   Parameter  Type   Description
   ========== ====== ========================
   error_code String Error codes of ModelArts
   error_msg  String Error message
   ========== ====== ========================

**Status code: 404**

.. table:: **Table 13** Response body parameters

   ========== ====== ========================
   Parameter  Type   Description
   ========== ====== ========================
   error_code String Error codes of ModelArts
   error_msg  String Error message
   ========== ====== ========================

Example Requests
----------------

.. code-block::

   https://v1/{project_id}/modelarts-pool/resource-instances/filter

   {
     "offset" : "100",
     "limit" : "100",
     "matches" : [ {
       "key" : "resource_name",
       "value" : "resource1"
     } ],
     "tags" : [ {
       "key" : "key1",
       "values" : [ "*value1", "value2" ]
     } ]
   }

Example Responses
-----------------

**Status code: 200**

Response to a normal request.

.. code-block::

   {
     "resources" : [ {
       "resource_detail" : null,
       "resource_id" : "6efce7bf-677d-400f-b451-3543ed997a24",
       "resource_name" : "service-79ca",
       "tags" : [ {
         "key" : "model_version",
         "value" : "0.1"
       }, {
         "key" : "gpu_type",
         "value" : "v100"
       } ]
     } ],
     "total_count" : 1000
   }

Status Codes
------------

=========== =============================
Status Code Description
=========== =============================
200         Response to a normal request.
400         Invalid parameters.
401         Authentication failed.
403         Insufficient permission.
404         Resource not found.
=========== =============================

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
