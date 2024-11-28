:original_name: ListAttachableObSs.html

.. _ListAttachableObSs:

Obtaining the Notebook Instances with OBS Storage Mounted
=========================================================

Function
--------

This API is used to obtain the notebook instances with OBS storage mounted.

Constraints
-----------

None

URI
---

GET /v1/{project_id}/notebooks/{instance_id}/storage

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                              |
   +=============+===========+========+==========================================================================================+
   | instance_id | Yes       | String | Notebook instance ID.                                                                    |
   +-------------+-----------+--------+------------------------------------------------------------------------------------------+
   | project_id  | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +-------------+-----------+--------+------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   +-----------+------------------------------------------------------------------------------------------------+--------------------------------+
   | Parameter | Type                                                                                           | Description                    |
   +===========+================================================================================================+================================+
   | current   | Integer                                                                                        | Current page                   |
   +-----------+------------------------------------------------------------------------------------------------+--------------------------------+
   | data      | Array of :ref:`DataVolumesRes <en-us_topic_0000002042806684__response_datavolumesres>` objects | Data                           |
   +-----------+------------------------------------------------------------------------------------------------+--------------------------------+
   | pages     | Integer                                                                                        | Total pages                    |
   +-----------+------------------------------------------------------------------------------------------------+--------------------------------+
   | size      | Integer                                                                                        | Number of records on each page |
   +-----------+------------------------------------------------------------------------------------------------+--------------------------------+
   | total     | Long                                                                                           | Total records                  |
   +-----------+------------------------------------------------------------------------------------------------+--------------------------------+

.. _en-us_topic_0000002042806684__response_datavolumesres:

.. table:: **Table 3** DataVolumesRes

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

   GET https://{endpoint}/v1/{project_id}/notebooks/{instance_id}/storage

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "current" : 1,
     "data" : [ {
       "id" : "91dd2d3f-2d92-475f-a375-04636af26cc9",
       "category" : "OBSFS",
       "mount_path" : "/data/wang/",
       "uri" : "obs://authoring-test/wang/",
       "status" : "MOUNTED"
     } ],
     "pages" : 1,
     "size" : 1,
     "total" : 1
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
