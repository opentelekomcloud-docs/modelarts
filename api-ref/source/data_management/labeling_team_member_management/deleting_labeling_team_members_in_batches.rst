.. _DeleteWorkers:

Deleting Labeling Team Members in Batches
=========================================

Function
--------

This API is used to delete labeling team members in batches.

URI
---

POST /v2/{project_id}/workforces/{workforce_id}/workers/batch-delete

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

   ========= ========= ================ ====================
   Parameter Mandatory Type             Description
   ========= ========= ================ ====================
   workers   No        Array of strings Team member ID list.
   ========= ========= ================ ====================

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------------------+-------------------------------------------------------------------------------+------------------------------------------------------------------------+
   | Parameter             | Type                                                                          | Description                                                            |
   +=======================+===============================================================================+========================================================================+
   | error_code            | String                                                                        | Error code.                                                            |
   +-----------------------+-------------------------------------------------------------------------------+------------------------------------------------------------------------+
   | error_msg             | String                                                                        | Error message.                                                         |
   +-----------------------+-------------------------------------------------------------------------------+------------------------------------------------------------------------+
   | results               | Array of :ref:`BatchResponse <deleteworkers__response_batchresponse>` objects | Result of deleting team members in batches.                            |
   +-----------------------+-------------------------------------------------------------------------------+------------------------------------------------------------------------+
   | success               | Boolean                                                                       | Check whether the operation is successful. The options are as follows: |
   |                       |                                                                               |                                                                        |
   |                       |                                                                               | -  **true**: The operation is successful.                              |
   |                       |                                                                               |                                                                        |
   |                       |                                                                               | -  **false**: The operation is failed.                                 |
   +-----------------------+-------------------------------------------------------------------------------+------------------------------------------------------------------------+

.. _deleteworkers__response_batchresponse:

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

Deleting Labeling Team Members in Batches

.. code-block::

   {
     "workers" : [ "89d4ae38431b8905449821605abdc3a9", "a2abd3f27b4e92c593c15282f8b6bd29" ]
   }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "success" : true,
     "results" : [ {
       "success" : true
     }, {
       "success" : true
     } ]
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
