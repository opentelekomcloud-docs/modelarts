.. _CreateWorkforceTask:

Creating a Team Labeling Task
=============================

Function
--------

This API is used to create a team labeling task.

URI
---

POST /v2/{project_id}/datasets/{dataset_id}/workforce-tasks

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                        |
   +============+===========+========+====================================================================================================================+
   | dataset_id | Yes       | String | Dataset ID.                                                                                                        |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <modelarts_03_0147>`. |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request body parameters

   +--------------------------------+-----------------+--------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter                      | Mandatory       | Type                                                                           | Description                                                                                                         |
   +================================+=================+================================================================================+=====================================================================================================================+
   | auto_sync_dataset              | No              | Boolean                                                                        | Whether to automatically synchronize the result of a team labeling task to the dataset. The options are as follows: |
   |                                |                 |                                                                                |                                                                                                                     |
   |                                |                 |                                                                                | -  **true**: Automatically synchronize the result of a team labeling task to the dataset. (Default value)           |
   |                                |                 |                                                                                |                                                                                                                     |
   |                                |                 |                                                                                | -  **false**: Do not automatically synchronize the result of a team labeling task to the dataset.                   |
   +--------------------------------+-----------------+--------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | data_sync_type                 | No              | Integer                                                                        | Synchronization type. The options are as follows:                                                                   |
   |                                |                 |                                                                                |                                                                                                                     |
   |                                |                 |                                                                                | -  **0**: not to be synchronized                                                                                    |
   |                                |                 |                                                                                |                                                                                                                     |
   |                                |                 |                                                                                | -  **1**: data to be synchronized                                                                                   |
   |                                |                 |                                                                                |                                                                                                                     |
   |                                |                 |                                                                                | -  **2**: label to be synchronized                                                                                  |
   |                                |                 |                                                                                |                                                                                                                     |
   |                                |                 |                                                                                | -  **3**: data and label to be synchronized                                                                         |
   +--------------------------------+-----------------+--------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | repetition                     | No              | Integer                                                                        | Number of persons who label each sample in a team labeling task. The minimum value is **1**.                        |
   +--------------------------------+-----------------+--------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | sample_conditions              | No              | String                                                                         | Search conditions of dataset samples. Samples that meet the conditions are filtered for team labeling.              |
   +--------------------------------+-----------------+--------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | synchronize_auto_labeling_data | No              | Boolean                                                                        | Whether to synchronize the auto labeling result of a team labeling task. The options are as follows:                |
   |                                |                 |                                                                                |                                                                                                                     |
   |                                |                 |                                                                                | -  **true**: Synchronize the results to be confirmed to team members after auto labeling is complete.               |
   |                                |                 |                                                                                |                                                                                                                     |
   |                                |                 |                                                                                | -  **false**: Do not synchronize the auto labeling results. (Default value)                                         |
   +--------------------------------+-----------------+--------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | workforces_config              | No              | :ref:`WorkforcesConfig <createworkforcetask__request_workforcesconfig>` object | Team labeling task information: Tasks can be assigned by the team administrator or a specified team.                |
   +--------------------------------+-----------------+--------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+

.. _createworkforcetask__request_workforcesconfig:

.. table:: **Table 3** WorkforcesConfig

   +------------+-----------+----------------------------------------------------------------------------------------+--------------------------------------------+
   | Parameter  | Mandatory | Type                                                                                   | Description                                |
   +============+===========+========================================================================================+============================================+
   | agency     | No        | String                                                                                 | Administrator.                             |
   +------------+-----------+----------------------------------------------------------------------------------------+--------------------------------------------+
   | workforces | No        | Array of :ref:`WorkforceConfig <createworkforcetask__request_workforceconfig>` objects | List of teams that execute labeling tasks. |
   +------------+-----------+----------------------------------------------------------------------------------------+--------------------------------------------+

.. _createworkforcetask__request_workforceconfig:

.. table:: **Table 4** WorkforceConfig

   +----------------+-----------+----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | Parameter      | Mandatory | Type                                                                 | Description                                                                                                                     |
   +================+===========+======================================================================+=================================================================================================================================+
   | workers        | No        | Array of :ref:`Worker <createworkforcetask__request_worker>` objects | List of labeling team members.                                                                                                  |
   +----------------+-----------+----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | workforce_id   | No        | String                                                               | ID of a labeling team.                                                                                                          |
   +----------------+-----------+----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | workforce_name | No        | String                                                               | Name of a labeling team. The value contains 0 to 1024 characters and does not support the following special characters: !<>=&"' |
   +----------------+-----------+----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------+

.. _createworkforcetask__request_worker:

.. table:: **Table 5** Worker

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                              |
   +=================+=================+=================+==========================================================================================================================================+
   | create_time     | No              | Long            | Creation time.                                                                                                                           |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | description     | No              | String          | Labeling team member description. The value contains 0 to 256 characters and does not support the following special characters: ^!<>=&"' |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | email           | No              | String          | Email address of a labeling team member.                                                                                                 |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | role            | No              | Integer         | Role. The options are as follows:                                                                                                        |
   |                 |                 |                 |                                                                                                                                          |
   |                 |                 |                 | -  **0**: labeling personnel                                                                                                             |
   |                 |                 |                 |                                                                                                                                          |
   |                 |                 |                 | -  **1**: reviewer                                                                                                                       |
   |                 |                 |                 |                                                                                                                                          |
   |                 |                 |                 | -  **2**: team administrator                                                                                                             |
   |                 |                 |                 |                                                                                                                                          |
   |                 |                 |                 | -  **3**: dataset owner                                                                                                                  |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | status          | No              | Integer         | Current login status of a labeling team member. The options are as follows:                                                              |
   |                 |                 |                 |                                                                                                                                          |
   |                 |                 |                 | -  **0**: The invitation email has not been sent.                                                                                        |
   |                 |                 |                 |                                                                                                                                          |
   |                 |                 |                 | -  **1**: The invitation email has been sent but the user has not logged in.                                                             |
   |                 |                 |                 |                                                                                                                                          |
   |                 |                 |                 | -  **2**: The user has logged in.                                                                                                        |
   |                 |                 |                 |                                                                                                                                          |
   |                 |                 |                 | -  **3**: The labeling team member has been deleted.                                                                                     |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | update_time     | No              | Long            | Update time.                                                                                                                             |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | worker_id       | No              | String          | ID of a labeling team member.                                                                                                            |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | workforce_id    | No              | String          | ID of a labeling team.                                                                                                                   |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 6** Response body parameters

   ========= ====== ===========================
   Parameter Type   Description
   ========= ====== ===========================
   task_id   String ID of a team labeling task.
   ========= ====== ===========================

Example Requests
----------------

Creating a Team Labeling Task

.. code-block::

   {
     "workspace_id" : "0",
     "task_name" : "task-eb17",
     "task_type" : 0,
     "description" : "",
     "version_id" : "",
     "labels" : [ {
       "name" : "Cat",
       "type" : 0,
       "property" : {
         "@modelarts:color" : "#3399ff"
       }
     }, {
       "name" : "Dog",
       "type" : 0,
       "property" : {
         "@modelarts:color" : "#3399ff"
       }
     } ],
     "synchronize_data" : false,
     "synchronize_auto_labeling_data" : false,
     "workforces_config" : {
       "workforces" : [ {
         "workforce_id" : "feSUo5NUIUnQAQNNTiS",
         "workers" : [ {
           "email" : "xxx@xxx.com"
         }, {
           "email" : "xxx@xxx.com"
         }, {
           "email" : "xxx@xxx.com"
         } ]
       } ]
     },
     "auto_sync_dataset" : false
   }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "task_id" : "6phXEto29utpaMwbQkg"
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
