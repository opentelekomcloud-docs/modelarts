:original_name: ShowLease.html

.. _ShowLease:

Querying the Available Duration of a Running Notebook Instance
==============================================================

Function
--------

This API is used to query the available duration of a running notebook instance.

Constraints
-----------

None

URI
---

GET /v1/{project_id}/notebooks/{id}/lease

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                              |
   +============+===========+========+==========================================================================================+
   | id         | Yes       | String | Notebook instance ID.                                                                    |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   +-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type    | Description                                                                                                                                                                                                        |
   +===========+=========+====================================================================================================================================================================================================================+
   | create_at | Long    | Time (UTC) when the instance is created, accurate to millisecond.                                                                                                                                                  |
   +-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | duration  | Long    | Instance running duration, which is calculated based on the instance creation time. If the instance creation time plus the duration is greater than the current time, the system automatically stops the instance. |
   +-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enable    | Boolean | Whether to enable auto stop of the instance.                                                                                                                                                                       |
   +-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type      | String  | Indicates the automatic stop type.                                                                                                                                                                                 |
   +-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | update_at | Long    | Time (UTC) when the instance is last updated (excluding the keepalive heartbeat time), accurate to millisecond.                                                                                                    |
   +-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

.. code-block:: text

   GET https://{endpoint}/v1/{project_id}/notebooks/{id}/lease

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "create_at" : 1638841744515,
     "duration" : 3600000,
     "enable" : true,
     "type" : "TIMING",
     "update_at" : 1638842905925
   }

Status Codes
------------

=========== ============
Status Code Description
=========== ============
200         OK
401         Unauthorized
403         Forbidden
404         Not Found
=========== ============

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
