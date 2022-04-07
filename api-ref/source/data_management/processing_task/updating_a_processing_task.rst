.. _UpdateProcessorTask:

Updating a Processing Task
==========================

Function
--------

This API is used to update a processing task. You can update feature analysis tasks and data processing tasks. Only the description of updated tasks is supported. You can specify the **task_id** path parameter to update a specific task.

URI
---

PUT /v2/{project_id}/processor-tasks/{task_id}

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                        |
   +============+===========+========+====================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <modelarts_03_0147>`. |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | task_id    | Yes       | String | ID of a data processing task.                                                                                      |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request body parameters

   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                                                         |
   +=============+===========+========+=====================================================================================================================================================+
   | description | No        | String | Description of a data processing task. The description contains 0 to 256 characters and does not support the following special characters: ^!<>=&"' |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Requests
----------------

Updating a Data Processing Task

.. code-block::

   {
     "description" : "test"
   }

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
404         Not Found
=========== ============

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
