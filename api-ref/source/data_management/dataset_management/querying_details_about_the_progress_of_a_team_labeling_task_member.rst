.. _GetWorkforceTaskMetrics:

Querying Details About the Progress of a Team Labeling Task Member
==================================================================

Function
--------

This API is used to query details about the progress of a team labeling task member.

URI
---

GET /v2/{project_id}/datasets/{dataset_id}/workforce-tasks/{workforce_task_id}/metrics

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

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   +--------------+---------------------------------+-------------------------------------------+
   | Parameter    | Type                            | Description                               |
   +==============+=================================+===========================================+
   | sample_stats | Map<String,Map<String,Integer>> | Statistics on team labeling task members. |
   +--------------+---------------------------------+-------------------------------------------+

Example Requests
----------------

Querying Details About the Progress of a Team Labeling Task Member

.. code-block::

   GET https://{endpoint}/v2/{project_id}/datasets/{dataset_id}/workforce-tasks/{workforce_task_id}/metrics

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "sample_stats" : {
       "xxx@xxx.com" : {
         "un_annotation" : 51,
         "rejected" : 0,
         "unreviewed" : 0,
         "accepted" : 0,
         "auto_annotation" : 0,
         "uncheck" : 0
       }
     }
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
