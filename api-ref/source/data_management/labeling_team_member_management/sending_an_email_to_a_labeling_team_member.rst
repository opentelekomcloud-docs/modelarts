:original_name: SendEmails.html

.. _SendEmails:

Sending an Email to a Labeling Team Member
==========================================

Function
--------

This API is used to send an email to a labeling team member.

URI
---

POST /v2/{project_id}/datasets/{dataset_id}/workforce-tasks/{workforce_task_id}/notify

.. table:: **Table 1** Path parameters

   +-------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory | Type   | Description                                                                                                        |
   +===================+===========+========+====================================================================================================================+
   | dataset_id        | Yes       | String | Dataset ID.                                                                                                        |
   +-------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | project_id        | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <modelarts_03_0147>`. |
   +-------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | workforce_task_id | Yes       | String | ID of a team labeling task.                                                                                        |
   +-------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request body parameters

   +-----------+-----------+------------------+---------------------------------------+
   | Parameter | Mandatory | Type             | Description                           |
   +===========+===========+==================+=======================================+
   | emails    | Yes       | Array of strings | Email list of a labeling team member. |
   +-----------+-----------+------------------+---------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------------------+----------------------------------------------------------------------------+------------------------------------------------------------------------+
   | Parameter             | Type                                                                       | Description                                                            |
   +=======================+============================================================================+========================================================================+
   | error_code            | String                                                                     | Error code.                                                            |
   +-----------------------+----------------------------------------------------------------------------+------------------------------------------------------------------------+
   | error_msg             | String                                                                     | Error message.                                                         |
   +-----------------------+----------------------------------------------------------------------------+------------------------------------------------------------------------+
   | results               | Array of :ref:`BatchResponse <sendemails__response_batchresponse>` objects | Result of sending an email to a labeling team member.                  |
   +-----------------------+----------------------------------------------------------------------------+------------------------------------------------------------------------+
   | success               | Boolean                                                                    | Check whether the operation is successful. The options are as follows: |
   |                       |                                                                            |                                                                        |
   |                       |                                                                            | -  **true**: The operation is successful.                              |
   |                       |                                                                            |                                                                        |
   |                       |                                                                            | -  **false**: The operation is failed.                                 |
   +-----------------------+----------------------------------------------------------------------------+------------------------------------------------------------------------+

.. _sendemails__response_batchresponse:

.. table:: **Table 4** BatchResponse

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

Sending an Email to a Labeling Team Member

.. code-block::

   {
     "emails" : [ "xxx@xxx.com", "xxx@xxx.com" ]
   }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "success" : true
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
