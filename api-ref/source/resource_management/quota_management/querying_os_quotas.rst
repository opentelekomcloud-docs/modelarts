:original_name: ShowOsQuota.html

.. _ShowOsQuota:

Querying OS Quotas
==================

Function
--------

Obtain the quotas of some resources in the ModelArts OS service, such as the resource pool quota and network quota.

Debugging
---------

You can debug this API through automatic authentication in or use the SDK sample code generated by API Explorer.

URI
---

GET /v1/{project_id}/quotas

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

   +-----------+----------------------------------------------------------------------+-----------------+
   | Parameter | Type                                                                 | Description     |
   +===========+======================================================================+=================+
   | quotas    | :ref:`quotas <en-us_topic_0000001910008068__response_quotas>` object | Resource quota. |
   +-----------+----------------------------------------------------------------------+-----------------+

.. _en-us_topic_0000001910008068__response_quotas:

.. table:: **Table 3** quotas

   +-----------+--------------------------------------------------------------------------------------+--------------------------------+
   | Parameter | Type                                                                                 | Description                    |
   +===========+======================================================================================+================================+
   | resources | Array of :ref:`resources <en-us_topic_0000001910008068__response_resources>` objects | Specifies the resource quotas. |
   +-----------+--------------------------------------------------------------------------------------+--------------------------------+

.. _en-us_topic_0000001910008068__response_resources:

.. table:: **Table 4** resources

   ========= ======= ================================================
   Parameter Type    Description
   ========= ======= ================================================
   type      String  Resource type.
   quota     Integer Specifies the upper limit of the resource quota.
   used      Integer Specifies used quotas.
   ========= ======= ================================================

**Status code: 404**

.. table:: **Table 5** Response body parameters

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
     "quotas" : {
       "resources" : [ {
         "type" : "pool",
         "quota" : 15,
         "used" : 10
       }, {
         "type" : "network",
         "quota" : 15,
         "used" : 10
       } ]
     }
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
