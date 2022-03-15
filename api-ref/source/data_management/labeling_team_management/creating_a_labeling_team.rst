Creating a Labeling Team
========================

Function
--------

This API is used to create a labeling team.

URI
---

POST /v2/{project_id}/workforces

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                                                |
   +============+===========+========+============================================================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see `Obtaining a Project ID <../../common_parameters/obtaining_a_project_id_and_name.html>`__. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------



.. _CreateWorkforcerequestCreateWorkforceReq:

.. table:: **Table 2** Request body parameters

   +----------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------+
   | Parameter      | Mandatory | Type   | Description                                                                                                                       |
   +================+===========+========+===================================================================================================================================+
   | description    | No        | String | Labeling team description. The value contains 0 to 256 characters and does not support the following special characters: ^!<>=&"' |
   +----------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------+
   | workforce_name | Yes       | String | Labeling team name. The value contains 1 to 64 characters, including only letters, digits, underscores (_), and hyphens (-).      |
   +----------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 201**



.. _CreateWorkforceresponseCreateWorkforceResp:

.. table:: **Table 3** Response body parameters

   ============ ====== ======================
   Parameter    Type   Description
   ============ ====== ======================
   workforce_id String ID of a labeling team.
   ============ ====== ======================

Example Requests
----------------

Creating a Labeling Team

.. code-block::

   {
     "workforce_name" : "team-123",
     "description" : "my team"
   }

Example Responses
-----------------

**Status code: 201**

Created

.. code-block::

   {
     "workforce_id" : "ZUH8gqkjuaib8pxkDdz"
   }

Status Codes
------------



.. _CreateWorkforcestatuscode:

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

See `Error Codes <../../common_parameters/error_codes.html>`__.

