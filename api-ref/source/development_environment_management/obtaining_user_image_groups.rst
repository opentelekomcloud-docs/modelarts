:original_name: ListImageGroup.html

.. _ListImageGroup:

Obtaining User Image Groups
===========================

Function
--------

Obtain the overview of user image information. The image name is used as the aggregated information.

Constraints
-----------

None

URI
---

GET /v1/{project_id}/images/group

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                              |
   +============+===========+========+==========================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter        | Mandatory       | Type            | Description                                                                                                                                   |
   +==================+=================+=================+===============================================================================================================================================+
   | name             | No              | String          | Image name, which contains a maximum of 512 characters, including lowercase letters, digits, hyphens (-), underscores (_), and periods (.)    |
   +------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | name_fuzzy_match | No              | Boolean         | Whether the image name is used for fuzzy match. The default value is **true**.                                                                |
   +------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | namespace        | No              | String          | Organization to which the image belongs. You can create and view the organization on the **Organization Management** page of the SWR console. |
   +------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | type             | No              | String          | Image type. Options:                                                                                                                          |
   |                  |                 |                 |                                                                                                                                               |
   |                  |                 |                 | -  **BUILD_IN**: built-in system image                                                                                                        |
   |                  |                 |                 |                                                                                                                                               |
   |                  |                 |                 | -  **DEDICATED**: private image                                                                                                               |
   +------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | workspace_id     | No              | String          | Workspace ID. If no workspaces are available, the default value is **0**.                                                                     |
   +------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------+----------------------------------------------------------------------------------------+--------------------------------+
   | Parameter | Type                                                                                   | Description                    |
   +===========+========================================================================================+================================+
   | current   | Integer                                                                                | Current page number.           |
   +-----------+----------------------------------------------------------------------------------------+--------------------------------+
   | data      | Array of :ref:`ImageGroup <en-us_topic_0000002079045725__response_imagegroup>` objects | Indicates the data.            |
   +-----------+----------------------------------------------------------------------------------------+--------------------------------+
   | pages     | Integer                                                                                | Total number of pages          |
   +-----------+----------------------------------------------------------------------------------------+--------------------------------+
   | size      | Integer                                                                                | Number of records on each page |
   +-----------+----------------------------------------------------------------------------------------+--------------------------------+
   | total     | Long                                                                                   | Total number of records        |
   +-----------+----------------------------------------------------------------------------------------+--------------------------------+

.. _en-us_topic_0000002079045725__response_imagegroup:

.. table:: **Table 4** ImageGroup

   +---------------+---------+--------------------------------------------------------------+
   | Parameter     | Type    | Description                                                  |
   +===============+=========+==============================================================+
   | name          | String  | The image name.                                              |
   +---------------+---------+--------------------------------------------------------------+
   | create_at     | Long    | Specifies the time (UTC ms) when the image is created.       |
   +---------------+---------+--------------------------------------------------------------+
   | namespace     | String  | Mirror the SWR organization described.                       |
   +---------------+---------+--------------------------------------------------------------+
   | update_at     | Long    | Specifies the time (UTC ms) when the image was last updated. |
   +---------------+---------+--------------------------------------------------------------+
   | version_count | Integer | Specifies the number of image versions.                      |
   +---------------+---------+--------------------------------------------------------------+

Example Requests
----------------

.. code-block:: text

   GET https://{endpoint}/v1/{project_id}/images/group

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "current" : 1,
     "data" : [ {
       "create_at" : 1652878011643,
       "name" : "123",
       "namespace" : "infer-model-dev",
       "update_at" : 1652878531791,
       "version_count" : 1
     }, {
       "create_at" : 1671708630448,
       "name" : "pytorch_1_8",
       "namespace" : "op_svc_modelarts_container2",
       "update_at" : 1671708630448,
       "version_count" : 1
     }, {
       "create_at" : 1671093486722,
       "name" : "mock-service-python",
       "namespace" : "mock-service1",
       "update_at" : 1671093486722,
       "version_count" : 1
     } ],
     "pages" : 1,
     "size" : 3,
     "total" : 3
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
