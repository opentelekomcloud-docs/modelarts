Stopping the Version of a Data Processing Task
==============================================

Function
--------

This API is used to stop the version of a data processing task.

URI
---

POST /v2/{project_id}/processor-tasks/{task_id}/versions/{version_id}/stop

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                                                |
   +============+===========+========+============================================================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see `Obtaining a Project ID <../../common_parameters/obtaining_a_project_id_and_name.html>`__. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | task_id    | Yes       | String | ID of a data processing task.                                                                                                                              |
   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version_id | Yes       | String | Version ID of a data processing task.                                                                                                                      |
   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

None

Example Requests
----------------

This API is used to stop the version of a data processing task.

.. code-block::

   POST https://{endpoint}/v2/{project_id}/processor-tasks/{task_id}/versions/{version_id}/stop

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   { }

Status Codes
------------



.. _StopProcessorTaskVersionstatuscode:

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

See `Error Codes <../../common_parameters/error_codes.html>`__.


