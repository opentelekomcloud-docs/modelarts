.. _UpdateWorker:

Updating a Labeling Team Member
===============================

Function
--------

This API is used to update a labeling team member.

URI
---

PUT /v2/{project_id}/workforces/{workforce_id}/workers/{worker_id}

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

.. table:: **Table 2** Request body parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                              |
   +=================+=================+=================+==========================================================================================================================================+
   | description     | No              | String          | Labeling team member description. The value contains 0 to 256 characters and does not support the following special characters: ^!<>=&"' |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | role            | No              | Integer         | Role. The options are as follows:                                                                                                        |
   |                 |                 |                 |                                                                                                                                          |
   |                 |                 |                 | -  **0**: labeling personnel                                                                                                             |
   |                 |                 |                 |                                                                                                                                          |
   |                 |                 |                 | -  **1**: reviewer                                                                                                                       |
   |                 |                 |                 |                                                                                                                                          |
   |                 |                 |                 | -  **2**: team administrator                                                                                                             |
   |                 |                 |                 |                                                                                                                                          |
   |                 |                 |                 | -  **3**: dataset owner                                                                                                                  |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Requests
----------------

Updating a Labeling Team Member

.. code-block::

   {
     "description" : "My name is Tom",
     "role" : 2
   }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   { }

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
