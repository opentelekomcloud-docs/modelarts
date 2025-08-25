:original_name: ShowAutoSearchTrials.html

.. _ShowAutoSearchTrials:

Querying All Trials Using Hyperparameter Search
===============================================

Function
--------

This API is used to query all trails using hyperparameter search.

URI
---

GET /v2/{project_id}/training-jobs/{training_job_id}/autosearch-trials

.. table:: **Table 1** Path Parameters

   +-----------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory | Type   | Description                                                                                                              |
   +=================+===========+========+==========================================================================================================================+
   | project_id      | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`.                                 |
   +-----------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | training_job_id | Yes       | String | Training job ID For details about how to obtain the value, see :ref:`Querying the Training Job List <listtrainingjobs>`. |
   +-----------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | project_id      | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`.                                 |
   +-----------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | training_job_id | Yes       | String | Training job ID For details about how to obtain the value, see :ref:`Querying the Training Job List <listtrainingjobs>`. |
   +-----------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   ========= ========= ======= ================================
   Parameter Mandatory Type    Description
   ========= ========= ======= ================================
   limit     No        Integer Number of returned data entries.
   offset    No        Integer Offset of a data entry.
   ========= ========= ======= ================================

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------+-------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | Parameter | Type                                                                                            | Description                                                                   |
   +===========+=================================================================================================+===============================================================================+
   | total     | Integer                                                                                         | Total number of trials using the hyperparameter search.                       |
   +-----------+-------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | count     | Integer                                                                                         | Number of hyperparameter search trials displayed on the current page.         |
   +-----------+-------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | limit     | Integer                                                                                         | Maximum number of hyperparameter search trials displayed on the current page. |
   +-----------+-------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | offset    | Integer                                                                                         | Current page for all trials searched using hyperparameters.                   |
   +-----------+-------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | group_by  | String                                                                                          | Grouping mode.                                                                |
   +-----------+-------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | items     | :ref:`items <en-us_topic_0000002374856541__en-us_topic_0000002091282817_response_items>` object | Hyperparameter search items.                                                  |
   +-----------+-------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------+

.. _en-us_topic_0000002374856541__en-us_topic_0000002091282817_response_items:

.. table:: **Table 4** items

   +-----------+----------------------+--------------------------------------------------------------+
   | Parameter | Type                 | Description                                                  |
   +===========+======================+==============================================================+
   | header    | Array of strings     | Fields of all trials searched using hyperparameters.         |
   +-----------+----------------------+--------------------------------------------------------------+
   | data      | Array<Array<String>> | Each data list of all trials searched using hyperparameters. |
   +-----------+----------------------+--------------------------------------------------------------+

Example Requests
----------------

The following shows how to query all trial information about the job whose **training_job_id** is **5b60a667-1438-4eb5-9705-85b860e623dc**.

.. code-block:: text

   GET https://endpoint/v2/{project_id}/training-jobs/5b60a667-1438-4eb5-9705-85b860e623dc/autosearch-trials

Example Responses
-----------------

**Status code: 200**

ok

.. code-block::

   {
     "total" : 8,
     "count" : 8,
     "limit" : 50,
     "offset" : 0,
     "group_by" : "",
     "items" : {
       "header" : [ "", "done", "pid", "config", "trial_id", "training_iteration", "time_total_s", "worker_index", "reward_attr", "status", "acc", "loss", "best_reward" ],
       "data" : [ [ "0", "True", "314", {
         "batch_size" : 32,
         "learning_rate" : 0.05512301741232006,
         "trial_index" : 0,
         "param/batch_size" : 32,
         "param/learning_rate" : 0.05512301741232006
       }, "ae544174", "2", "19.477163314819336", "", "0.0625", "TERMINATED", "0.0625", "tensor(0.0754, device='cuda:0', requires_grad=True)", "0.0625" ], [ "1", "True", "315", {
         "batch_size" : 32,
         "learning_rate" : 0.0785570955603036,
         "trial_index" : 1,
         "param/batch_size" : 32,
         "param/learning_rate" : 0.0785570955603036
       }, "ae548666", "2", "3.601897954940796", "", "0.0", "TERMINATED", "0.0", "tensor(0.0760, device='cuda:0', requires_grad=True)", "0.0" ], [ "2", "True", "312", {
         "batch_size" : 16,
         "learning_rate" : 0.04015387428829642,
         "trial_index" : 2,
         "param/batch_size" : 16,
         "param/learning_rate" : 0.04015387428829642
       }, "ae54c0ea", "2", "3.5978384017944336", "", "0.1875", "TERMINATED", "0.1875", "tensor(0.1469, device='cuda:0', requires_grad=True)", "0.1875" ], [ "3", "True", "313", {
         "batch_size" : 32,
         "learning_rate" : 0.0340820322164706,
         "trial_index" : 3,
         "param/batch_size" : 32,
         "param/learning_rate" : 0.0340820322164706
       }, "ae5503c0", "2", "3.641200304031372", "", "0.25", "TERMINATED", "0.25", "tensor(0.0716, device='cuda:0', requires_grad=True)", "0.25" ], [ "4", "True", "470", {
         "batch_size" : 32,
         "learning_rate" : 0.03656488928171769,
         "trial_index" : 4,
         "param/batch_size" : 32,
         "param/learning_rate" : 0.03656488928171769
       }, "bef46590", "2", "3.6120550632476807", "", "0.09375", "TERMINATED", "0.09375", "tensor(0.0740, device='cuda:0', requires_grad=True)", "0.09375" ], [ "5", "True", "499", {
         "batch_size" : 32,
         "learning_rate" : 0.008413169003970163,
         "trial_index" : 5,
         "param/batch_size" : 32,
         "param/learning_rate" : 0.008413169003970163
       }, "bef578f4", "2", "3.6379287242889404", "", "0.1875", "TERMINATED", "0.1875", "tensor(0.0723, device='cuda:0', requires_grad=True)", "0.1875" ], [ "6", "True", "528", {
         "batch_size" : 64,
         "learning_rate" : 0.06297447200613912,
         "trial_index" : 6,
         "param/batch_size" : 64,
         "param/learning_rate" : 0.06297447200613912
       }, "bef5c584", "2", "3.711118221282959", "", "0.046875", "TERMINATED", "0.046875", "tensor(0.0381, device='cuda:0', requires_grad=True)", "0.046875" ], [ "7", "True", "557", {
         "batch_size" : 32,
         "learning_rate" : 0.04426479392014276,
         "trial_index" : 7,
         "param/batch_size" : 32,
         "param/learning_rate" : 0.04426479392014276
       }, "bef60684", "2", "3.6971280574798584", "", "0.0625", "TERMINATED", "0.0625", "tensor(0.0778, device='cuda:0', requires_grad=True)", "0.0625" ] ]
     }
   }

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
200         ok
=========== ===========

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
