.. _UpdateWorkspaceQuotas:

Modifying a Workspace Quota
===========================

Function
--------

This API is used to modify a workspace quota.

URI
---

PUT /v1/{project_id}/workspaces/{workspace_id}/quotas

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

.. table:: **Table 2** Request body parameters

   +-----------+-----------+------------------------------------------------------------------------+----------------+
   | Parameter | Mandatory | Type                                                                   | Description    |
   +===========+===========+========================================================================+================+
   | quotas    | Yes       | Array of :ref:`quotas <updateworkspacequotas__request_quotas>` objects | List of quotas |
   +-----------+-----------+------------------------------------------------------------------------+----------------+

.. _updateworkspacequotas__request_quotas:

.. table:: **Table 3** quotas

   +-----------+-----------+---------+----------------------------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                                          |
   +===========+===========+=========+======================================================================+
   | resource  | Yes       | String  | Unique resource ID                                                   |
   +-----------+-----------+---------+----------------------------------------------------------------------+
   | quota     | Yes       | Integer | Current quota. Value **-1** indicates that the quota is not limited. |
   +-----------+-----------+---------+----------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------+-------------------------------------------------------------------------+----------------+
   | Parameter | Type                                                                    | Description    |
   +===========+=========================================================================+================+
   | quotas    | Array of :ref:`quotas <updateworkspacequotas__response_quotas>` objects | List of quotas |
   +-----------+-------------------------------------------------------------------------+----------------+

.. _updateworkspacequotas__response_quotas:

.. table:: **Table 5** quotas

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

Example Requests
----------------

Modifying Workspace Quotas

.. code-block::

   PUT  https://{endpoint}/v1/{project_id}/workspaces/{workspace_id}/quotas

   {
     "quotas" : [ {
       "workspace_id" : "***9cd9ea8a5432cbcd6496e57839***",
       "resource" : "exemlProject.gpu_duration",
       "quota" : 10
     } ]
   }

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
       "update_time" : 1470000020000
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
