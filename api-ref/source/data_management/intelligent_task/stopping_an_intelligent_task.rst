.. _StopAutoAnnotation:

Stopping an Intelligent Task
============================

Function
--------

This API is used to stop intelligent tasks, including auto labeling, one-click model deployment, and auto grouping tasks. You can specify the **task_id** parameter to stop a specific task.

URI
---

POST /v2/{project_id}/datasets/{dataset_id}/tasks/{task_id}/stop

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                        |
   +============+===========+========+====================================================================================================================+
   | dataset_id | Yes       | String | Dataset ID.                                                                                                        |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <modelarts_03_0147>`. |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | task_id    | Yes       | String | Task ID.                                                                                                           |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

None

Example Requests
----------------

Stopping Auto Labeling, One-Click Model Deployment, or Auto Grouping Tasks

.. code-block::

   POST https://{endpoint}/v2/{project_id}/datasets/{dataset_id}/tasks/{task_id}/stop

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
404         Not Found
=========== ============

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
