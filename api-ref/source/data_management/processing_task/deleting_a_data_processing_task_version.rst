.. _DeleteProcessorTaskVersion:

Deleting a Data Processing Task Version
=======================================

Function
--------

This API is used to delete a data processing task version.

URI
---

DELETE /v2/{project_id}/processor-tasks/{task_id}/versions/{version_id}

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                        |
   +============+===========+========+====================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <modelarts_03_0147>`. |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | task_id    | Yes       | String | ID of a data processing task.                                                                                      |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | version_id | Yes       | String | Version ID of a data processing task.                                                                              |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

None

Example Requests
----------------

Deleting a Data Processing Task Version

.. code-block::

   DELETE https://{endpoint}/v2/{project_id}/processor-tasks/{task_id}/versions/{version_id}

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
