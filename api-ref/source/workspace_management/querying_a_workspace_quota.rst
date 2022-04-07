.. _ListWorkspaceQuotas:

Querying a Workspace Quota
==========================

Function
--------

This API is used to obtain workspace quotas.

URI
---

GET /v1/{project_id}/workspaces/{workspace_id}/quotas

.. table:: **Table 1** Path parameters

   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                        |
   +==============+===========+========+====================================================================================================================+
   | project_id   | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <modelarts_03_0147>`. |
   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | workspace_id | Yes       | String | Workspace ID.                                                                                                      |
   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   +-----------+-----------------------------------------------------------------------+----------------+
   | Parameter | Type                                                                  | Description    |
   +===========+=======================================================================+================+
   | quotas    | Array of :ref:`quotas <listworkspacequotas__response_quotas>` objects | List of quotas |
   +-----------+-----------------------------------------------------------------------+----------------+

.. _listworkspacequotas__response_quotas:

.. table:: **Table 3** quotas

   +-------------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Type    | Description                                                                                                                                     |
   +=============+=========+=================================================================================================================================================+
   | name_en     | String  | Name of a quota, in English                                                                                                                     |
   +-------------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | name_cn     | String  | Name of a quota, in Chinese                                                                                                                     |
   +-------------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | resource    | String  | Unique resource ID                                                                                                                              |
   +-------------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | quota       | Integer | Existing quota. Value **-1** indicates that the quota is not limited.                                                                           |
   +-------------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | min_quota   | Integer | Minimum quota                                                                                                                                   |
   +-------------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | max_quota   | Integer | Maximum quota                                                                                                                                   |
   +-------------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | unit_en     | String  | Quota unit, in English                                                                                                                          |
   +-------------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | unit_cn     | String  | Quota unit, in Chinese                                                                                                                          |
   +-------------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | update_time | Number  | Last modification time, in UTC format. If the resource quota has not been modified, the default value is the time when a workspace was created. |
   +-------------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | used_quota  | Number  | Used quota. If the value of **quota** is **-1** (indicating that the quota is not limited), the **used_quota** value is **null**.               |
   +-------------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

Querying Workspace Quotas

.. code-block::

   GET https://{endpoint}/v1/{project_id}/workspaces/{workspace_id}/quotas

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "quotas" : [ {
       "name_en" : "ExeMLtraining duration (image classification, object detection, and soundclassification)",
       "name_cn" : "Chinese name of the quota",
       "resource" : "exemlProject.gpu_duration",
       "quota" : 10,
       "min_quota" : -1,
       "max_quota" : 60000,
       "unit_en" : "minute",
       "unit_cn" : "Chinese name of the minute",
       "update_time" : 1470000020000,
       "used_quota" : 5
     } ]
   }

Status Codes
------------

=========== ===================
Status Code Description
=========== ===================
200         OK
400         BadRequest
403         Forbidden
500         InternalServerError
=========== ===================

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
