:original_name: modelarts_03_0409.html

.. _modelarts_03_0409:

Configuring Authorization
=========================

Function
--------

This API is used to configure ModelArts authorization. ModelArts functions such as training management, development environment, data management, and real-time services can be properly used only after required authorization is configured. This API allows the system administrator to configure an agency for IAM users and set an access key of the current user.

URI
---

POST /v2/{project_id}/authorizations

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                      |
   +============+===========+========+==================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <modelarts_03_0147>`. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request body parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                     |
   +=================+=================+=================+=================================================================================================================================================================+
   | user_id         | No              | String          | User ID. For details about how to obtain a user ID, see :ref:`Obtaining a User ID <modelarts_03_0006>`.                                                         |
   |                 |                 |                 |                                                                                                                                                                 |
   |                 |                 |                 | If **user_id** is set to **all-users**, authorization is configured for all IAM users. If some users have been authorized, their authorization will be updated. |
   |                 |                 |                 |                                                                                                                                                                 |
   |                 |                 |                 | This parameter is mandatory only if the authorization method is set to **Agency**.                                                                              |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type            | No              | String          | Authorization type. **Agency** is recommended.                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                 |
   |                 |                 |                 | Options:                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                 |
   |                 |                 |                 | -  **agency**: authorization through an agency                                                                                                                  |
   |                 |                 |                 | -  **credential**: authorization through an access Key (AK/SK)                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                 |
   |                 |                 |                 | Default: **agency**                                                                                                                                             |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | content         | Yes             | String          | Authorization content.                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                 |
   |                 |                 |                 | -  If **Authorization Type** is set to **Agency**, this field indicates the agency name.                                                                        |
   |                 |                 |                 | -  If **Authorization Type** is set to **AK/SK**, this field indicates the access key ID (AK).                                                                  |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | secret_key      | No              | String          | Secret Access Key (SK). This field is required only when **Authorization Method** is set to **AK/SK**.                                                          |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Requests
----------------

Upload authorization.

.. code-block:: text

   POST https://{endpoint}/v2/{project_id}/authorizations

   {
     "user_id" : "****d80fb058844ae8b82aa66d9fe****",
     "type" : "agency",
     "content" : "modelarts_agency"
   }

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

See :ref:`Error Codes <modelarts_03_0095>`.
