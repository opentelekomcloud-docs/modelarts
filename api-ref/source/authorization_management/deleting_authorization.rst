Deleting Authorization
======================

Function
--------

This API is used to delete the authorization of a specified user or all users.

URI
---

DELETE /v2/{project_id}/authorizations

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                                           |
   +============+===========+========+=======================================================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain a project ID, see `Obtaining a Project ID <../common_parameters/obtaining_a_project_id_and_name.html>`__. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                       |
   +===========+===========+========+===================================================================================================+
   | user_id   | No        | String | User ID. If this parameter is set to **all**, the authorization of all IAM users will be deleted. |
   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

None

Example Requests
----------------

Delete the authorization of a specified user.

.. code-block::

   DELETE https://{endpoint}/v2/{project_id}/authorizations?user_id=****d80fb058844ae8b82aa66d9fe****

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "result" : "true"
   }

Status Codes
------------



.. _DeleteAuthorizationsstatuscode:

=========== ============
Status Code Description
=========== ============
200         OK
400         Bad Request
401         Unauthorized
403         Forbidden
404         Not Found
=========== ============

Error Codes
-----------

See `Error Codes <../common_parameters/error_codes.html>`__.


