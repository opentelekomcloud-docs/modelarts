:original_name: RenewLease.html

.. _RenewLease:

Prolonging a Notebook Instance
==============================

Function
--------

This API is used to prolong a notebook instance.

Constraints
-----------

None

URI
---

PATCH /v1/{project_id}/notebooks/{id}/lease

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+---------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                     |
   +============+===========+========+=================================================================================+
   | id         | Yes       | String | Notebook instance ID.                                                           |
   +------------+-----------+--------+---------------------------------------------------------------------------------+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID <modelarts_03_0147>`. |
   +------------+-----------+--------+---------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   ========= ========= ==== =================================
   Parameter Mandatory Type Description
   ========= ========= ==== =================================
   duration  Yes       Long Renewal duration, in milliseconds
   ========= ========= ==== =================================

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Type    | Description                                                                                                                                                                                                        |
   +=============+=========+====================================================================================================================================================================================================================+
   | create_time | Long    | Time (UTC) when the instance is created, accurate to millisecond.                                                                                                                                                  |
   +-------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | duration    | Long    | Instance running duration, which is calculated based on the instance creation time. If the instance creation time plus the duration is greater than the current time, the system automatically stops the instance. |
   +-------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enable      | Boolean | Whether to enable auto stop of the instance.                                                                                                                                                                       |
   +-------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | update_time | Long    | Time (UTC) when the instance is last updated (excluding the keepalive heartbeat time), accurate to millisecond.                                                                                                    |
   +-------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

None

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "create_at" : 1638841744515,
     "duration" : 3600000,
     "enable" : true,
     "update_at" : 1638843018759
   }

Status Codes
------------

=========== ============
Status Code Description
=========== ============
200         OK
204         No Content
401         Unauthorized
403         Forbidden
=========== ============

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
