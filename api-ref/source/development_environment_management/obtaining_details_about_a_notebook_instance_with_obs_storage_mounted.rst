:original_name: ShowAttachableObs.html

.. _ShowAttachableObs:

Obtaining Details About a Notebook Instance with OBS Storage Mounted
====================================================================

Function
--------

This API is used to obtain details about a notebook instance with OBS storage mounted.

Constraints
-----------

None

URI
---

GET /v1/{project_id}/notebooks/{instance_id}/storage/{storage_id}

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

   GET https://{endpoint}/v1/{project_id}/notebooks/{instance_id}/storage/{storage_id}

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "id" : "91dd2d3f-2d92-475f-a375-04636af26cc9",
     "category" : "OBSFS",
     "mount_path" : "/data/wang/",
     "uri" : "obs://authoring-test/wang/",
     "status" : "MOUNTED"
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
