.. _GetDatasetMetrics:

Querying the Monitoring Data of a Dataset
=========================================

Function
--------

This API is used to query the monitoring data of a dataset within a specified time range.

URI
---

GET /v2/{project_id}/datasets/{dataset_id}/metrics

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                        |
   +============+===========+========+====================================================================================================================+
   | dataset_id | Yes       | String | Dataset ID.                                                                                                        |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <modelarts_03_0147>`. |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +-------------------+-----------+--------+-------------------------------------------+
   | Parameter         | Mandatory | Type   | Description                               |
   +===================+===========+========+===========================================+
   | end_time          | Yes       | Long   | End time of the monitoring information.   |
   +-------------------+-----------+--------+-------------------------------------------+
   | start_time        | Yes       | Long   | Start time of the monitoring information. |
   +-------------------+-----------+--------+-------------------------------------------+
   | workforce_task_id | No        | String | ID of a team labeling task.               |
   +-------------------+-----------+--------+-------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------+---------------------------------+---------------------------------+
   | Parameter | Type                            | Description                     |
   +===========+=================================+=================================+
   | metrics   | Map<String,Map<String,Integer>> | Dataset monitoring information. |
   +-----------+---------------------------------+---------------------------------+

Example Requests
----------------

Querying the Monitoring Data of a Dataset

.. code-block::

   GET https://{endpoint}/v2/{project_id}/datasets/{dataset_id}/metrics

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "metrics" : {
       "un_annotation" : {
         "1606233612612" : 16,
         "1606320012681" : 16
       },
       "failed_user" : { },
       "total" : {
         "1606233612612" : 16,
         "1606320012681" : 16
       },
       "queuing" : { },
       "success" : { },
       "unfinished" : { },
       "manual_annotation" : {
         "1606233612612" : 0,
         "1606320012681" : 0
       },
       "failed" : { },
       "failed_system" : { }
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
