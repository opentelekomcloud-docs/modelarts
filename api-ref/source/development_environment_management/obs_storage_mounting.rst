:original_name: AttachObs.html

.. _AttachObs:

OBS Storage Mounting
====================

Function
--------

An OBS parallel file system can be mounted to a specified file directory of a running notebook instance. After the mounting, objects in the OBS parallel file system can be read and written in the container as a file system.

Constraints
-----------

None

URI
---

POST /v1/{project_id}/notebooks/{instance_id}/storage

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                             |
   +=============+===========+========+=========================================================================================================+
   | instance_id | Yes       | String | Notebook instance ID, which can be obtained by calling the API for querying the notebook instance list. |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | project_id  | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`.                |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request body parameters

   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                  |
   +============+===========+========+==============================================================================================================+
   | category   | No        | String | Storage type The value can be OBS.                                                                           |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------+
   | mount_path | No        | String | Path mounted to the notebook instance. The path must be in the /data/ subdirectory of the notebook instance. |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------+
   | uri        | No        | String | OBS object path, for example, **obs://modelarts/notebook/**.                                                 |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

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

The following is an example of how to dynamically mount an OBS parallel file system to the **/data/wang/** directory in the instance.

.. code-block::

   {
     "category" : "OBS",
     "mount_path" : "/data/wang/",
     "uri" : "obs://authoring-test/wang/"
   }

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
     "status" : "MOUNTING"
   }

Status Codes
------------

=========== ============
Status Code Description
=========== ============
200         OK
201         Created
401         Unauthorized
403         Forbidden
404         Not Found
=========== ============

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
