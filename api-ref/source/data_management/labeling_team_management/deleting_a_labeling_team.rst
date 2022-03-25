Deleting a Labeling Team
========================

Function
--------

This API is used to delete a labeling team.

URI
---

DELETE /v2/{project_id}/workforces/{workforce_id}

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

None

Response Parameters
-------------------

**Status code: 204**



.. _DeleteWorkforceresponseDeleteWorkforceResp:

.. table:: **Table 2** Response body parameters

   +-----------------------+----------------------------------------------------------------------------+------------------------------------------------------------------------+
   | Parameter             | Type                                                                       | Description                                                            |
   +=======================+============================================================================+========================================================================+
   | error_code            | String                                                                     | Error code.                                                            |
   +-----------------------+----------------------------------------------------------------------------+------------------------------------------------------------------------+
   | error_msg             | String                                                                     | Error message.                                                         |
   +-----------------------+----------------------------------------------------------------------------+------------------------------------------------------------------------+
   | results               | Array of `BatchResponse <#deleteworkforceresponsebatchresponse>`__ objects | Result of deleting team members in batches.                            |
   +-----------------------+----------------------------------------------------------------------------+------------------------------------------------------------------------+
   | success               | Boolean                                                                    | Check whether the operation is successful. The options are as follows: |
   |                       |                                                                            |                                                                        |
   |                       |                                                                            | -  **true**: The operation is successful.                              |
   |                       |                                                                            |                                                                        |
   |                       |                                                                            | -  **false**: The operation is failed.                                 |
   +-----------------------+----------------------------------------------------------------------------+------------------------------------------------------------------------+



.. _DeleteWorkforceresponseBatchResponse:

.. table:: **Table 3** BatchResponse

   +-----------------------+-----------------------+------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                            |
   +=======================+=======================+========================================================================+
   | error_code            | String                | Error code.                                                            |
   +-----------------------+-----------------------+------------------------------------------------------------------------+
   | error_msg             | String                | Error message.                                                         |
   +-----------------------+-----------------------+------------------------------------------------------------------------+
   | success               | Boolean               | Check whether the operation is successful. The options are as follows: |
   |                       |                       |                                                                        |
   |                       |                       | -  **true**: The operation is successful.                              |
   |                       |                       |                                                                        |
   |                       |                       | -  **false**: The operation is failed.                                 |
   +-----------------------+-----------------------+------------------------------------------------------------------------+

Example Requests
----------------

Deleting a Labeling Team

.. code-block::

   DELETE https://{endpoint}/v2/{project_id}/workforces/{workforce_id}

Example Responses
-----------------

**Status code: 204**

No Content

.. code-block::

   { }

Status Codes
------------



.. _DeleteWorkforcestatuscode:

=========== ============
Status Code Description
=========== ============
204         No Content
401         Unauthorized
403         Forbidden
=========== ============

Error Codes
-----------

See `Error Codes <../../common_parameters/error_codes.html>`__.


