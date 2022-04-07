.. _StartWorkforceSamplingTask:

Creating a Team Labeling Acceptance Task
========================================

Function
--------

This API is used to create a team labeling acceptance task.

URI
---

POST /v2/{project_id}/datasets/{dataset_id}/workforce-tasks/{workforce_task_id}/acceptance

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

   +---------------+-----------+---------+-------------------------------------------------------------------------------------------------------------------------------+
   | Parameter     | Mandatory | Type    | Description                                                                                                                   |
   +===============+===========+=========+===============================================================================================================================+
   | sampling_num  | No        | Integer | Number of samples for the acceptance task. Either this parameter or the sampling ratio is delivered.                          |
   +---------------+-----------+---------+-------------------------------------------------------------------------------------------------------------------------------+
   | sampling_rate | No        | Double  | Sampling ratio of the acceptance task. The value range is (0,1]. Either this parameter or the number of samples is delivered. |
   +---------------+-----------+---------+-------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   ========= ====== ======================================
   Parameter Type   Description
   ========= ====== ======================================
   task_id   String ID of an asynchronous acceptance task.
   ========= ====== ======================================

Example Requests
----------------

Creating a Team Labeling Acceptance Task and Setting the Sampling Percentage to 20%

.. code-block::

   {
     "sampling_rate" : 0.2
   }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "task_id" : "nv6BbozxCJmZcHAE9hV"
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
