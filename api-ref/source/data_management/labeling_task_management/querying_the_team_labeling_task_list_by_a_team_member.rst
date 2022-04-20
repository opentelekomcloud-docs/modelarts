.. _ListWorkerTasks:

Querying the Team Labeling Task List by a Team Member
=====================================================

Function
--------

This API is used to query the team labeling task list by a team member.

URI
---

GET /v2/{project_id}/workforces/worker-tasks

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
   | order           | No              | String          | Sorting method. The options are as follows:                                                                   |
   |                 |                 |                 |                                                                                                               |
   |                 |                 |                 | -  **asc**: ascending order                                                                                   |
   |                 |                 |                 |                                                                                                               |
   |                 |                 |                 | -  **desc**: descending order (default value)                                                                 |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------+
   | search_content  | No              | String          | Fuzzy search keyword. By default, this parameter is left blank.                                               |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------+
   | sort_by         | No              | String          | Sorting mode of the query. The options are as follows:                                                        |
   |                 |                 |                 |                                                                                                               |
   |                 |                 |                 | -  **create_time**: Sort by creation time. (Default value)                                                    |
   |                 |                 |                 |                                                                                                               |
   |                 |                 |                 | -  **workforce_task_name**: Sort by task name.                                                                |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +--------------+---------------------------------------------------------------------------+------------------------------------------+
   | Parameter    | Type                                                                      | Description                              |
   +==============+===========================================================================+==========================================+
   | count        | Integer                                                                   | Total number of team labeling tasks.     |
   +--------------+---------------------------------------------------------------------------+------------------------------------------+
   | worker_tasks | Array of :ref:`WorkerTask <listworkertasks__response_workertask>` objects | Team labeling task list queried by page. |
   +--------------+---------------------------------------------------------------------------+------------------------------------------+

.. _listworkertasks__response_workertask:

.. table:: **Table 4** WorkerTask

   +-----------------------+-------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                              | Description                                                                                      |
   +=======================+===================================================================+==================================================================================================+
   | create_time           | Long                                                              | Time when a labeling team member's task is created.                                              |
   +-----------------------+-------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
   | dataset_id            | String                                                            | ID of a dataset associated with a labeling team member's task.                                   |
   +-----------------------+-------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
   | dataset_type          | Integer                                                           | Labeling type of a team member's task.                                                           |
   +-----------------------+-------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
   | email                 | String                                                            | Email address of a labeling team member.                                                         |
   +-----------------------+-------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
   | email_status          | Integer                                                           | Email notification status of a labeling team member's labeling task. The options are as follows: |
   |                       |                                                                   |                                                                                                  |
   |                       |                                                                   | -  **0**: The email has not been sent.                                                           |
   |                       |                                                                   |                                                                                                  |
   |                       |                                                                   | -  **1**: The email format is incorrect.                                                         |
   |                       |                                                                   |                                                                                                  |
   |                       |                                                                   | -  **2**: The email address is unreachable.                                                      |
   |                       |                                                                   |                                                                                                  |
   |                       |                                                                   | -  **3**: The email has been sent.                                                               |
   +-----------------------+-------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
   | last_notify_time      | Long                                                              | Timestamp of the latest notification email sent to a labeling team member.                       |
   +-----------------------+-------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
   | pass_rate             | Double                                                            | Pass rate of task acceptance review for a labeling team member.                                  |
   +-----------------------+-------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
   | role                  | Integer                                                           | Role of a labeling team member.                                                                  |
   +-----------------------+-------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
   | sample_stats          | :ref:`SampleStats <listworkertasks__response_samplestats>` object | Sample statistics of a labeling team member's task.                                              |
   +-----------------------+-------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
   | score                 | Double                                                            | Average acceptance score of labeling team members' task samples.                                 |
   +-----------------------+-------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
   | task_id               | String                                                            | Team labeling task ID associated with a member's task.                                           |
   +-----------------------+-------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
   | task_status           | Integer                                                           | Task status of a labeling team member. The options are as follows:                               |
   |                       |                                                                   |                                                                                                  |
   |                       |                                                                   | -  **6**: created                                                                                |
   |                       |                                                                   |                                                                                                  |
   |                       |                                                                   | -  **0**: starting                                                                               |
   |                       |                                                                   |                                                                                                  |
   |                       |                                                                   | -  **1**: running                                                                                |
   |                       |                                                                   |                                                                                                  |
   |                       |                                                                   | -  **2**: under acceptance                                                                       |
   |                       |                                                                   |                                                                                                  |
   |                       |                                                                   | -  **3**: approved, indicating the team labeling task is complete                                |
   |                       |                                                                   |                                                                                                  |
   |                       |                                                                   | -  **4**: rejected, indicating that the task needs to be labeled and reviewed again              |
   +-----------------------+-------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
   | update_time           | Long                                                              | Time when a labeling team member's task is updated.                                              |
   +-----------------------+-------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
   | worker_id             | String                                                            | ID of a labeling team member.                                                                    |
   +-----------------------+-------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
   | workforce_task_name   | String                                                            | Team labeling task name associated with a member's task.                                         |
   +-----------------------+-------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+

.. _listworkertasks__response_samplestats:

.. table:: **Table 5** SampleStats

   +------------------------------+---------+-----------------------------------------------------------------------------------------------------+
   | Parameter                    | Type    | Description                                                                                         |
   +==============================+=========+=====================================================================================================+
   | accepted_sample_count        | Integer | Number of samples accepted by the owner.                                                            |
   +------------------------------+---------+-----------------------------------------------------------------------------------------------------+
   | auto_annotation_sample_count | Integer | Number of samples to be confirmed after intelligent labeling.                                       |
   +------------------------------+---------+-----------------------------------------------------------------------------------------------------+
   | deleted_sample_count         | Integer | Number of deleted samples.                                                                          |
   +------------------------------+---------+-----------------------------------------------------------------------------------------------------+
   | rejected_sample_count        | Integer | Number of samples that failed to pass the owner acceptance.                                         |
   +------------------------------+---------+-----------------------------------------------------------------------------------------------------+
   | sampled_sample_count         | Integer | Number of samples that are to be accepted by the owner and sampled.                                 |
   +------------------------------+---------+-----------------------------------------------------------------------------------------------------+
   | total_sample_count           | Integer | Total number of samples.                                                                            |
   +------------------------------+---------+-----------------------------------------------------------------------------------------------------+
   | unannotated_sample_count     | Integer | Number of unlabeled samples.                                                                        |
   +------------------------------+---------+-----------------------------------------------------------------------------------------------------+
   | uncheck_sample_count         | Integer | Number of samples that have been approved by the reviewer and are to be accepted by the owner.      |
   +------------------------------+---------+-----------------------------------------------------------------------------------------------------+
   | unreviewed_sample_count      | Integer | Number of samples that have been labeled by the labeler but have not been reviewed by the reviewer. |
   +------------------------------+---------+-----------------------------------------------------------------------------------------------------+

Example Requests
----------------

Querying the Team Labeling Task List by a Team Member

.. code-block::

   GET https://{endpoint}/v2/{project_id}/workforces/worker-tasks?offset=0&limit=10&sort_by=create_time&order=desc&filePreview=false

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "count" : 2,
     "worker_tasks" : [ {
       "email" : "xxx@xxx.com",
       "worker_id" : "8c15ad080d3eabad14037b4eb00d6a6f",
       "role" : 0,
       "task_id" : "tY330MHxV9dqIPVaTRM",
       "workforce_task_name" : "task-cd60",
       "dataset_id" : "WxCREuCkBSAlQr9xrde",
       "sample_stats" : {
         "total_sample_count" : 309,
         "unannotated_sample_count" : 308,
         "unreviewed_sample_count" : 0,
         "uncheck_sample_count" : 1,
         "sampled_sample_count" : 0,
         "rejected_sample_count" : 0,
         "accepted_sample_count" : 0,
         "auto_annotation_sample_count" : 0
       },
       "create_time" : 1606224714358,
       "update_time" : 1606224878490,
       "email_status" : 3,
       "last_notify_time" : 0,
       "dataset_type" : 1,
       "task_status" : 1,
       "user" : {
         "domainId" : "04f924738800d3270fc0c013a47363a0",
         "domainName" : "test_123",
         "projectId" : "04f924739300d3272fc3c013e36bb4b8",
         "userId" : "04f924743b00d4331f31c0131ada6769",
         "userName" : "test_123"
       }
     }, {
       "email" : "xxx@xxx.com",
       "worker_id" : "8c15ad080d3eabad14037b4eb00d6a6f",
       "role" : 0,
       "task_id" : "MJVjCQDMso95a8dvUm4",
       "workforce_task_name" : "task-2720",
       "dataset_id" : "OY82gjEHxt9w1efgrhS",
       "sample_stats" : {
         "total_sample_count" : 50005,
         "unannotated_sample_count" : 50005,
         "unreviewed_sample_count" : 0,
         "uncheck_sample_count" : 0,
         "sampled_sample_count" : 0,
         "rejected_sample_count" : 0,
         "accepted_sample_count" : 0,
         "auto_annotation_sample_count" : 0
       },
       "create_time" : 1605949737134,
       "update_time" : 1605949737134,
       "email_status" : 3,
       "last_notify_time" : 0,
       "dataset_type" : 0,
       "task_status" : 2,
       "user" : {
         "domainId" : "04f924738800d3270fc0c013a47363a0",
         "domainName" : "test_123",
         "projectId" : "04f924739300d3272fc3c013e36bb4b8",
         "userId" : "04f924743b00d4331f31c0131ada6769",
         "userName" : "test_123"
       }
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
