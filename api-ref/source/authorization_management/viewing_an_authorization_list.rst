.. _GetAuthorizations:

Viewing an Authorization List
=============================

Function
--------

This API is used to view an authorization list.

URI
---

GET /v2/{project_id}/authorizations

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                      |
   +============+===========+========+==================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <modelarts_03_0147>`. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                              |
   +=================+=================+=================+==========================================================================+
   | sort_by         | No              | String          | Sorting field.                                                           |
   |                 |                 |                 |                                                                          |
   |                 |                 |                 | Options:                                                                 |
   |                 |                 |                 |                                                                          |
   |                 |                 |                 | -  **user_name**: IAM user                                               |
   |                 |                 |                 |                                                                          |
   |                 |                 |                 | -  **create_time**: creation time                                        |
   |                 |                 |                 |                                                                          |
   |                 |                 |                 | Default: **user_name**                                                   |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------+
   | order           | No              | String          | Sorting method.                                                          |
   |                 |                 |                 |                                                                          |
   |                 |                 |                 | Options:                                                                 |
   |                 |                 |                 |                                                                          |
   |                 |                 |                 | -  **asc**: ascending order                                              |
   |                 |                 |                 |                                                                          |
   |                 |                 |                 | -  **desc**: descending order                                            |
   |                 |                 |                 |                                                                          |
   |                 |                 |                 | Default: **asc**                                                         |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------+
   | limit           | No              | Integer         | Maximum number of records returned on each page. Default value: **1000** |
   |                 |                 |                 |                                                                          |
   |                 |                 |                 | The value ranges from 1 to 1000.                                         |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------+
   | offset          | No              | Integer         | Start page of the paging list. The default value is **0**.               |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-------------+---------------------------------------------------------------------------------------------------+---------------------------------+
   | Parameter   | Type                                                                                              | Description                     |
   +=============+===================================================================================================+=================================+
   | total_count | Number                                                                                            | Authorization information.      |
   +-------------+---------------------------------------------------------------------------------------------------+---------------------------------+
   | auth        | Array of :ref:`AuthorizationResponse <getauthorizations__response_authorizationresponse>` objects | Authorization information list. |
   +-------------+---------------------------------------------------------------------------------------------------+---------------------------------+

.. _getauthorizations__response_authorizationresponse:

.. table:: **Table 4** AuthorizationResponse

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                        |
   +=======================+=======================+====================================================================================================================================================+
   | user_id               | String                | User ID. For details about how to obtain a user ID, see :ref:`Obtaining a User ID <modelarts_03_0006>`.                                            |
   |                       |                       |                                                                                                                                                    |
   |                       |                       | If **user_id** is set to **all**, all IAM users are authorized. If some IAM users have been authorized, the authorization setting will be updated. |
   |                       |                       |                                                                                                                                                    |
   |                       |                       | This parameter is mandatory only if the authorization type is set to **agency**.                                                                   |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | type                  | String                | Authorization type. **Agency** is recommended.                                                                                                     |
   |                       |                       |                                                                                                                                                    |
   |                       |                       | Options:                                                                                                                                           |
   |                       |                       |                                                                                                                                                    |
   |                       |                       | -  **agency**: authorization through an agency                                                                                                     |
   |                       |                       |                                                                                                                                                    |
   |                       |                       | -  **credential**: authorization through an access Key (AK/SK)                                                                                     |
   |                       |                       |                                                                                                                                                    |
   |                       |                       | Default: **agency**                                                                                                                                |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | content               | String                | Authorization content.                                                                                                                             |
   |                       |                       |                                                                                                                                                    |
   |                       |                       | -  If **Authorization Type** is set to **Agency**, this field indicates the agency name.                                                           |
   |                       |                       |                                                                                                                                                    |
   |                       |                       | -  If **Authorization Type** is set to **AK/SK**, this field indicates the access key ID (AK).                                                     |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | secret_key            | String                | Secret Access Key (SK). This field is required only when **Authorization Method** is set to **AK/SK**.                                             |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time           | Long                  | Timestamp when the quality job was created.                                                                                                        |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

View an authorization list.

.. code-block::

   GET https://{endpoint}/v2/{project_id}/authorizations

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "total_count" : 1,
     "auth" : [ {
       "user_id" : "****d80fb058844ae8b82aa66d9fe****",
       "user_name" : "iam-user01",
       "type" : "agency",
       "content" : "modelarts_agency",
       "create_time" : 15657747821288
     } ]
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
