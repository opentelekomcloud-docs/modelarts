:original_name: DeleteProcessorTask.html

.. _DeleteProcessorTask:

Deleting a Processing Task
==========================

Function
--------

This API is used to delete a processing task, including feature analysis tasks and data processing tasks. A specific task can be deleted by specifying the **task_id** parameter.

Debugging
---------

You can debug this API through automatic authentication in or use the SDK sample code generated by API Explorer.

URI
---

DELETE /v2/{project_id}/processor-tasks/{task_id}

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                               |
   +============+===========+========+===========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+
   | task_id    | Yes       | String | ID of a data processing task.                                                                                             |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

None

Example Requests
----------------

Deleting a Data Processing Task

.. code-block:: text

   DELETE https://{endpoint}/v2/{project_id}/processor-tasks/{task_id}

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   { }

Status Codes
------------

=========== ============
Status Code Description
=========== ============
200         OK
401         Unauthorized
403         Forbidden
=========== ============

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
