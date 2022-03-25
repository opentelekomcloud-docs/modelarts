Deleting a Processing Task
==========================

Function
--------

This API is used to delete a processing task. You can delete feature analysis tasks and data processing tasks. A specific task can be deleted by specifying the **task_id** path parameter.

URI
---

DELETE /v2/{project_id}/processor-tasks/{task_id}

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                                                |
   +============+===========+========+============================================================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see `Obtaining a Project ID <../../common_parameters/obtaining_a_project_id_and_name.html>`__. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | task_id    | Yes       | String | ID of a data processing task.                                                                                                                              |
   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

None

Example Requests
----------------

Deleting a Data Processing Task

.. code-block::

   DELETE https://{endpoint}/v2/{project_id}/processor-tasks/{task_id}

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   { }

Status Codes
------------



.. _DeleteProcessorTaskstatuscode:

=========== ============
Status Code Description
=========== ============
200         OK
401         Unauthorized
403         Forbidden
=========== ============

Error Codes
-----------

See `Error Codes <../../common_parameters/error_codes.html>`__.


