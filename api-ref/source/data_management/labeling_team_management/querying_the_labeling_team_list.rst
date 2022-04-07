.. _ListWorkforces:

Querying the Labeling Team List
===============================

Function
--------

This API is used to query the labeling team list.

URI
---

GET /v2/{project_id}/workforces

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                        |
   +============+===========+========+====================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <modelarts_03_0147>`. |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory       | Type            | Description                                                                                                   |
   +===================+=================+=================+===============================================================================================================+
   | limit             | No              | Integer         | Maximum number of records returned on each page. The value ranges from 1 to 100. The default value is **10**. |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------+
   | offset            | No              | Integer         | Start page of the paging list. The default value is **0**.                                                    |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------+
   | order             | No              | String          | Sorting sequence of the query. The options are as follows:                                                    |
   |                   |                 |                 |                                                                                                               |
   |                   |                 |                 | -  **asc**: ascending order                                                                                   |
   |                   |                 |                 |                                                                                                               |
   |                   |                 |                 | -  **desc**: descending order (default value)                                                                 |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------+
   | search_content    | No              | String          | Fuzzy search keyword. By default, this parameter is left blank.                                               |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------+
   | sort_by           | No              | String          | Sorting mode of the query. The options are as follows:                                                        |
   |                   |                 |                 |                                                                                                               |
   |                   |                 |                 | -  **create_time**: Sort by creation time. (Default value)                                                    |
   |                   |                 |                 |                                                                                                               |
   |                   |                 |                 | -  **workforce_name**: Sort by labeling team name.                                                            |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------+
   | workforce_task_id | No              | String          | ID of a team labeling task.                                                                                   |
   +-------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +--------------+------------------------------------------------------------------------+-------------------------------------+
   | Parameter    | Type                                                                   | Description                         |
   +==============+========================================================================+=====================================+
   | total_number | Integer                                                                | Total number of labeling teams.     |
   +--------------+------------------------------------------------------------------------+-------------------------------------+
   | workforces   | Array of :ref:`Workforce <listworkforces__response_workforce>` objects | Labeling team list queried by page. |
   +--------------+------------------------------------------------------------------------+-------------------------------------+

.. _listworkforces__response_workforce:

.. table:: **Table 4** Workforce

   +----------------+---------+---------------------------------------------------------------------------------------------------------------------------------+
   | Parameter      | Type    | Description                                                                                                                     |
   +================+=========+=================================================================================================================================+
   | create_time    | Long    | Time when a labeling team is created.                                                                                           |
   +----------------+---------+---------------------------------------------------------------------------------------------------------------------------------+
   | description    | String  | Description of a labeling team.                                                                                                 |
   +----------------+---------+---------------------------------------------------------------------------------------------------------------------------------+
   | update_time    | Long    | Time when a labeling team is updated.                                                                                           |
   +----------------+---------+---------------------------------------------------------------------------------------------------------------------------------+
   | worker_count   | Integer | Total number of labeling team members.                                                                                          |
   +----------------+---------+---------------------------------------------------------------------------------------------------------------------------------+
   | workforce_id   | String  | ID of a labeling team.                                                                                                          |
   +----------------+---------+---------------------------------------------------------------------------------------------------------------------------------+
   | workforce_name | String  | Name of a labeling team.                                                                                                        |
   +----------------+---------+---------------------------------------------------------------------------------------------------------------------------------+
   | workspace_id   | String  | Workspace ID. If no workspace is created, the default value is **0**. If a workspace is created and used, use the actual value. |
   +----------------+---------+---------------------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

Querying the Labeling Team List

.. code-block::

   GET https://{endpoint}/v2/{project_id}/workforces

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "total_number" : 2,
     "workforces" : [ {
       "workforce_id" : "ZUH8gqkjuaib8pxkDdz",
       "workforce_name" : "team-123",
       "description" : "my team",
       "worker_count" : 0,
       "create_time" : 1606354772548,
       "update_time" : 1606354772548
     }, {
       "workforce_id" : "3Ry04NsqvEybuWYLDvC",
       "workforce_name" : "team-170a",
       "description" : "",
       "worker_count" : 1,
       "create_time" : 1604644946891,
       "update_time" : 1606238678626
     } ]
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
