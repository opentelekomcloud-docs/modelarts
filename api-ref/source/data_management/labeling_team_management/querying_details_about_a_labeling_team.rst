.. _DescWorkforce:

Querying Details About a Labeling Team
======================================

Function
--------

This API is used to query the details about a labeling team.

URI
---

GET /v2/{project_id}/workforces/{workforce_id}

.. table:: **Table 1** Path parameters

   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                        |
   +==============+===========+========+====================================================================================================================+
   | project_id   | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <modelarts_03_0147>`. |
   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | workforce_id | Yes       | String | ID of a labeling team.                                                                                             |
   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   +----------------+---------+---------------------------------------------------------------------------------------------------------------------------------+
   | Parameter      | Type    | Description                                                                                                                     |
   +================+=========+=================================================================================================================================+
   | create_time    | Long    | Time when a labeling team is created.                                                                                           |
   +----------------+---------+---------------------------------------------------------------------------------------------------------------------------------+
   | description    | String  | Description of a labeling team.                                                                                                 |
   +----------------+---------+---------------------------------------------------------------------------------------------------------------------------------+
   | update_time    | Long    | Time when a labeling team is updated.                                                                                           |
   +----------------+---------+---------------------------------------------------------------------------------------------------------------------------------+
   | worker_count   | Integer | Total number of labeling team members.                                                                                          |
   +----------------+---------+---------------------------------------------------------------------------------------------------------------------------------+
   | workforce_id   | String  | ID of a labeling team.                                                                                                          |
   +----------------+---------+---------------------------------------------------------------------------------------------------------------------------------+
   | workforce_name | String  | Name of a labeling team.                                                                                                        |
   +----------------+---------+---------------------------------------------------------------------------------------------------------------------------------+
   | workspace_id   | String  | Workspace ID. If no workspace is created, the default value is **0**. If a workspace is created and used, use the actual value. |
   +----------------+---------+---------------------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

Querying Details About a Labeling Team

.. code-block::

   GET https://{endpoint}/v2/{project_id}/workforces/{workforce_id}

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "workforce_id" : "gyb7IaAvkLc5IhEY2dv",
     "workforce_name" : "team-aed7",
     "description" : "",
     "worker_count" : 2,
     "create_time" : 1575104620882,
     "update_time" : 1575104620882
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
