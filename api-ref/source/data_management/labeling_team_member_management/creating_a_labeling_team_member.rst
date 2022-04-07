.. _CreateWorker:

Creating a Labeling Team Member
===============================

Function
--------

This API is used to create a labeling team member.

URI
---

POST /v2/{project_id}/workforces/{workforce_id}/workers

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

.. table:: **Table 2** Request body parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                      |
   +=================+=================+=================+==================================================================================================================================+
   | description     | No              | String          | Member description. The description contains 0 to 256 characters and does not support the following special characters: ^!<>=&"' |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------+
   | emails          | Yes             | String          | Email address of a labeling team member.                                                                                         |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------+
   | role            | Yes             | Integer         | Member role. The options are as follows:                                                                                         |
   |                 |                 |                 |                                                                                                                                  |
   |                 |                 |                 | -  **0**: labeling personnel                                                                                                     |
   |                 |                 |                 |                                                                                                                                  |
   |                 |                 |                 | -  **1**: reviewer                                                                                                               |
   |                 |                 |                 |                                                                                                                                  |
   |                 |                 |                 | -  **2**: team administrator                                                                                                     |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Requests
----------------

Creating a Labeling Team Member

.. code-block::

   {
     "emails" : "xxx@xxx.com",
     "description" : "",
     "role" : "2"
   }

Example Responses
-----------------

**Status code: 201**

Created

.. code-block::

   { }

Status Codes
------------

=========== ============
Status Code Description
=========== ============
201         Created
401         Unauthorized
403         Forbidden
404         Not Found
=========== ============

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
