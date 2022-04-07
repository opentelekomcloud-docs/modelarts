.. _DeleteWorkforceTask:

Deleting a Team Labeling Task
=============================

Function
--------

This API is used to delete a team labeling task.

URI
---

DELETE /v2/{project_id}/datasets/{dataset_id}/workforce-tasks/{workforce_task_id}

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

None

Example Requests
----------------

Deleting a Team Labeling Task

.. code-block::

   DELETE https://{endpoint}/v2/{project_id}/datasets/{dataset_id}/workforce-tasks/{workforce_task_id}

Example Responses
-----------------

**Status code: 204**

No Content

.. code-block::

   { }

Status Codes
------------

=========== ============
Status Code Description
=========== ============
204         No Content
401         Unauthorized
403         Forbidden
=========== ============

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
