Updating a Labeling Team
========================

Function
--------

This API is used to update a labeling team.

URI
---

PUT /v2/{project_id}/workforces/{workforce_id}

.. table:: **Table 1** Path parameters

   +--------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                |
   +==============+===========+========+============================================================================================================================================================+
   | project_id   | Yes       | String | Project ID. For details about how to obtain the project ID, see `Obtaining a Project ID <../../common_parameters/obtaining_a_project_id_and_name.html>`__. |
   +--------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | workforce_id | Yes       | String | ID of a labeling team.                                                                                                                                     |
   +--------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------



.. _UpdateWorkforcerequestUpdateWorkforceReq:

.. table:: **Table 2** Request body parameters

   +----------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter      | Mandatory | Type   | Description                                                                                                                            |
   +================+===========+========+========================================================================================================================================+
   | description    | No        | String | Labeling team description. The value contains 0 to 256 characters and does not support the following special characters: ^!<>=&"'      |
   +----------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------+
   | workforce_name | No        | String | Name of a labeling team. The value contains 1 to 64 characters and only letters, digits, hyphens (-), and underscores (_) are allowed. |
   +----------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Requests
----------------

Updating a Labeling Team

.. code-block::

   {
     "description" : "my team"
   }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   { }

Status Codes
------------



.. _UpdateWorkforcestatuscode:

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

See `Error Codes <../../common_parameters/error_codes.html>`__.

