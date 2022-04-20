.. _ListAllWorkers:

Querying the List of All Labeling Team Members
==============================================

Function
--------

This API is used to query the list of all labeling team members.

URI
---

GET /v2/{project_id}/workforces/workers

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                        |
   +============+===========+========+====================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <modelarts_03_0147>`. |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                   |
   +=================+=================+=================+===============================================================================================================+
   | limit           | No              | Integer         | Maximum number of records returned on each page. The value ranges from 1 to 100. The default value is **10**. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------+
   | offset          | No              | Integer         | Start page of the paging list. The default value is **0**.                                                    |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------+
   | order           | No              | String          | Sorting sequence of the query. The options are as follows:                                                    |
   |                 |                 |                 |                                                                                                               |
   |                 |                 |                 | -  **asc**: ascending order                                                                                   |
   |                 |                 |                 |                                                                                                               |
   |                 |                 |                 | -  **desc**: descending order (default value)                                                                 |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------+
   | role            | No              | Integer         | Filtering query based on the member role. The options are as follows:                                         |
   |                 |                 |                 |                                                                                                               |
   |                 |                 |                 | -  **0**: labeling personnel (default value)                                                                  |
   |                 |                 |                 |                                                                                                               |
   |                 |                 |                 | -  **1**: reviewer                                                                                            |
   |                 |                 |                 |                                                                                                               |
   |                 |                 |                 | -  **2**: team administrator                                                                                  |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------+
   | sort_by         | No              | String          | Sorting mode of the query. The options are as follows:                                                        |
   |                 |                 |                 |                                                                                                               |
   |                 |                 |                 | -  **create_time**: Sort by creation time. (Default value)                                                    |
   |                 |                 |                 |                                                                                                               |
   |                 |                 |                 | -  **email**: Sort by email.                                                                                  |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +--------------+------------------------------------------------------------------+---------------------------------------------+
   | Parameter    | Type                                                             | Description                                 |
   +==============+==================================================================+=============================================+
   | total_number | Integer                                                          | Total number of labeling team members.      |
   +--------------+------------------------------------------------------------------+---------------------------------------------+
   | workers      | Array of :ref:`Worker <listallworkers__response_worker>` objects | Labeling team members list queried by page. |
   +--------------+------------------------------------------------------------------+---------------------------------------------+

.. _listallworkers__response_worker:

.. table:: **Table 4** Worker

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                              |
   +=======================+=======================+==========================================================================================================================================+
   | create_time           | Long                  | Creation time.                                                                                                                           |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                | Labeling team member description. The value contains 0 to 256 characters and does not support the following special characters: ^!<>=&"' |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | email                 | String                | Email address of a labeling team member.                                                                                                 |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | role                  | Integer               | Role. The options are as follows:                                                                                                        |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  **0**: labeling personnel                                                                                                             |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  **1**: reviewer                                                                                                                       |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  **2**: team administrator                                                                                                             |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  **3**: dataset owner                                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | status                | Integer               | Current login status of a labeling team member. The options are as follows:                                                              |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  **0**: The invitation email has not been sent.                                                                                        |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  **1**: The invitation email has been sent but the user has not logged in.                                                             |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  **2**: The user has logged in.                                                                                                        |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  **3**: The labeling team member has been deleted.                                                                                     |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | update_time           | Long                  | Update time.                                                                                                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | worker_id             | String                | ID of a labeling team member.                                                                                                            |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | workforce_id          | String                | ID of a labeling team.                                                                                                                   |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

Querying All Labeling Team Administrators

.. code-block::

   GET https://{endpoint}/v2/{project_id}/workforces/workers??role=2

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "total_number" : 2,
     "workers" : [ {
       "email" : "xxx@xxx.com",
       "worker_id" : "df40e4afcb793d13f01f6c9022341e6f",
       "workforce_id" : "feSUo5NUIUnQAQNNTiS",
       "status" : 0,
       "role" : 2,
       "description" : "",
       "create_time" : 1595927749772,
       "update_time" : 1595927749772
     }, {
       "email" : "xxx@xxx.com",
       "worker_id" : "27906df1d06c0827b7c24f761d618541",
       "workforce_id" : "XiL5RcHmxyIt3aYIOtI",
       "status" : 0,
       "role" : 2,
       "description" : "",
       "create_time" : 1590027298717,
       "update_time" : 1590027298717
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
