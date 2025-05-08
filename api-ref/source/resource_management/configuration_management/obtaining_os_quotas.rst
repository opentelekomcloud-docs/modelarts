:original_name: ShowOsQuota.html

.. _ShowOsQuota:

Obtaining OS Quotas
===================

Function
--------

This API is used to obtain the quotas of some ModelArts OS resources, such as the quotas for resource pools and networks.

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
   | quotas    | :ref:`quotas <en-us_topic_0000002233721414__response_quotas>` object | Resource quotas |
   +-----------+----------------------------------------------------------------------+-----------------+

.. _en-us_topic_0000002233721414__response_quotas:

.. table:: **Table 3** quotas

   +-----------+--------------------------------------------------------------------------------------+----------------------------+
   | Parameter | Type                                                                                 | Description                |
   +===========+======================================================================================+============================+
   | resources | Array of :ref:`resources <en-us_topic_0000002233721414__response_resources>` objects | Resource quota information |
   +-----------+--------------------------------------------------------------------------------------+----------------------------+

.. _en-us_topic_0000002233721414__response_resources:

.. table:: **Table 4** resources

   ========= ======= =================================
   Parameter Type    Description
   ========= ======= =================================
   type      String  Resource type
   quota     Integer Upper limit of the resource quota
   used      Integer Used quota
   ========= ======= =================================

**Status code: 404**

.. table:: **Table 5** Response body parameters

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
200         OK
404         Not found
=========== ===========

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
