.. _DescWorker:

Querying Details About Labeling Team Members
============================================

Function
--------

This API is used to query details about labeling team members.

URI
---

GET /v2/{project_id}/workforces/{workforce_id}/workers/{worker_id}

.. table:: **Table 1** Path parameters

   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                        |
   +==============+===========+========+====================================================================================================================+
   | project_id   | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <modelarts_03_0147>`. |
   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | worker_id    | Yes       | String | ID of a labeling team member.                                                                                      |
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

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                              |
   +=======================+=======================+==========================================================================================================================================+
   | create_time           | Long                  | Creation time.                                                                                                                           |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                | Labeling team member description. The value contains 0 to 256 characters and does not support the following special characters: ^!<>=&"' |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | email                 | String                | Email address of a labeling team member.                                                                                                 |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | role                  | Integer               | Role. The options are as follows:                                                                                                        |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  **0**: labeling personnel                                                                                                             |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  **1**: reviewer                                                                                                                       |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  **2**: team administrator                                                                                                             |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  **3**: dataset owner                                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | status                | Integer               | Current login status of a labeling team member. The options are as follows:                                                              |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  **0**: The invitation email has not been sent.                                                                                        |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  **1**: The invitation email has been sent but the user has not logged in.                                                             |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  **2**: The user has logged in.                                                                                                        |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  **3**: The labeling team member has been deleted.                                                                                     |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | update_time           | Long                  | Update time.                                                                                                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | worker_id             | String                | ID of a labeling team member.                                                                                                            |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | workforce_id          | String                | ID of a labeling team.                                                                                                                   |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

Querying Details About Labeling Team Members

.. code-block::

   GET https://{endpoint}/v2/{project_id}/workforces/{workforce_id}/workers/{worker_id}

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "email" : "xxx@xxx.com",
     "worker_id" : "b1e4054407ecb36a7bcde70f52ba37f2",
     "workforce_id" : "gyb7IaAvkLc5IhEY2dv",
     "status" : 0,
     "role" : 2,
     "description" : "",
     "create_time" : 1606356324223,
     "update_time" : 1606356324223
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
