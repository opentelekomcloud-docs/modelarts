:original_name: CancelObs.html

.. _CancelObs:

Unmounting OBS Storage from a Notebook Instance
===============================================

Function
--------

This API is used to unmount OBS storage from a notebook instance. After OBS storage is unmounted, OBS objects remain unchanged but cannot be operated in the notebook container.

Constraints
-----------

None

URI
---

DELETE /v1/{project_id}/notebooks/{instance_id}/storage/{storage_id}

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                              |
   +=============+===========+========+==========================================================================================+
   | instance_id | Yes       | String | Notebook instance ID.                                                                    |
   +-------------+-----------+--------+------------------------------------------------------------------------------------------+
   | project_id  | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +-------------+-----------+--------+------------------------------------------------------------------------------------------+
   | storage_id  | Yes       | String | OBS storage ID.                                                                          |
   +-------------+-----------+--------+------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   +-----------------------+-----------------------+-----------------------------------------------------------+
   | Parameter             | Type                  | Description                                               |
   +=======================+=======================+===========================================================+
   | category              | String                | Storage type The value can be OBS.                        |
   +-----------------------+-----------------------+-----------------------------------------------------------+
   | id                    | String                | ID of the instance with OBS storage mounted.              |
   +-----------------------+-----------------------+-----------------------------------------------------------+
   | mount_path            | String                | Path where OBS storage is mounted to a notebook instance. |
   +-----------------------+-----------------------+-----------------------------------------------------------+
   | status                | String                | Status of OBS storage to be mounted. Options:             |
   |                       |                       |                                                           |
   |                       |                       | -  **MOUNTING**: being mounted                            |
   |                       |                       |                                                           |
   |                       |                       | -  **MOUNT_FAILED**: mounting failed                      |
   |                       |                       |                                                           |
   |                       |                       | -  **MOUNTED**: mounted                                   |
   |                       |                       |                                                           |
   |                       |                       | -  **UNMOUNTING**: being unmounted                        |
   |                       |                       |                                                           |
   |                       |                       | -  **UNMOUNT_FAILED**: unmounting failed                  |
   |                       |                       |                                                           |
   |                       |                       | -  **UNMOUNTED**: unmounted                               |
   +-----------------------+-----------------------+-----------------------------------------------------------+
   | uri                   | String                | OBS object path                                           |
   +-----------------------+-----------------------+-----------------------------------------------------------+

Example Requests
----------------

.. code-block:: text

   DELETE https://{endpoint}/v1/{project_id}/notebooks/{instance_id}/storage/{storage_id}

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "category" : "OBSFS",
     "id" : "91dd2d3f-2d92-475f-a375-04636af26cc9",
     "mount_path" : "/data/wang/",
     "status" : "UNMOUNTING",
     "uri" : "obs://authoring-test/wang/"
   }

Status Codes
------------

=========== ============
Status Code Description
=========== ============
200         OK
204         No Content
401         Unauthorized
403         Forbidden
=========== ============

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
