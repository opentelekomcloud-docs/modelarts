:original_name: StopTask.html

.. _StopTask:

Stopping a Service Task
=======================

Function
--------

This API is used to stop a service task. This parameter applies only to IEF. It cannot be used in ModelArts Edge.

URI
---

POST /v1/{project_id}/services/{service_id}/tasks/{task_id}/stop

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                              |
   +============+===========+========+==========================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | service_id | Yes       | String | Service ID                                                                               |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | task_id    | Yes       | String | ID of a specified service task                                                           |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 400**

.. table:: **Table 2** Response body parameters

   ========== ====== ===========================
   Parameter  Type   Description
   ========== ====== ===========================
   error_code String Internal service error code
   error_msg  String Error message
   ========== ====== ===========================

**Status code: 404**

.. table:: **Table 3** Response body parameters

   ========== ====== ===========================
   Parameter  Type   Description
   ========== ====== ===========================
   error_code String Internal service error code
   error_msg  String Error message
   ========== ====== ===========================

Example Requests
----------------

Stop a specified service task.

.. code-block::

   /v1/b722xxxxxxxxxxxxxxxxxxxxxxeb4674/services/88bbxxxx-xxxx-xxxx-xxxx-xxxxxxxxbcfe/tasks/53e4xxxxxxxxxxxxxxxxxxxxxxb55b3e/stop

Example Responses
-----------------

**Status code: 400**

The request is invalid.

.. code-block::

   {
     "error_code" : "ModelArts.0101",
     "error_msg" : "Invalid argument. parameter [task_id] does not match ^[0-9a-f]{32}$."
   }

**Status code: 404**

The specified service does not exist.

.. code-block::

   {
     "error_code" : "ModelArts.3502",
     "error_msg" : "Service 2a2db77f-xxxx-xxxx-xxxx-608a31865313 does not exist."
   }

Status Codes
------------

=========== ==========================================================
Status Code Description
=========== ==========================================================
202         The request for stopping a service task has been accepted.
400         The request is invalid.
404         The specified service does not exist.
=========== ==========================================================

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
