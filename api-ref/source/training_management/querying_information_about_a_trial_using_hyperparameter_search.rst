:original_name: ShowAutoSearchPerTrial.html

.. _ShowAutoSearchPerTrial:

Querying Information About a Trial Using Hyperparameter Search
==============================================================

Function
--------

This API is used to query information about a trial using hyperparameter search based on the **trial_id**.

URI
---

GET /v2/{project_id}/training-jobs/{training_job_id}/autosearch-trials/{trial_id}

.. table:: **Table 1** Path Parameters

   +-----------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory | Type   | Description                                                                                                              |
   +=================+===========+========+==========================================================================================================================+
   | project_id      | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`.                                 |
   +-----------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | training_job_id | Yes       | String | Training job ID For details about how to obtain the value, see :ref:`Querying the Training Job List <listtrainingjobs>`. |
   +-----------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | trial_id        | Yes       | String | **trial_id** for hyperparameter search.                                                                                  |
   +-----------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   +-----------+----------------------+-----------------------------------------------------------+
   | Parameter | Type                 | Description                                               |
   +===========+======================+===========================================================+
   | header    | Array of strings     | Field of a trial searched using hyperparameters.          |
   +-----------+----------------------+-----------------------------------------------------------+
   | data      | Array<Array<String>> | Each data list of a trial searched using hyperparameters. |
   +-----------+----------------------+-----------------------------------------------------------+

Example Requests
----------------

The following shows how to query information about trial **ae544174** of the job whose **training_job_id** is **5b60a667-1438-4eb5-9705-85b860e623dc**.

.. code-block:: text

   GET https://endpoint//v2/{project_id}/training-jobs/5b60a667-1438-4eb5-9705-85b860e623dc/autosearch-trials/ae544174

Example Responses
-----------------

**Status code: 200**

ok

.. code-block::

   {
     "header" : [ "done", "pid", "best_reward", "time_total_s", "config", "acc", "loss", "trial_id", "training_iteration", "reward_attr" ],
     "data" : [ [ "False", "314", "0.0625", "19.477163314819336", {
       "batch_size" : 32,
       "learning_rate" : 0.05512301741232006,
       "trial_index" : 0,
       "param/batch_size" : 32,
       "param/learning_rate" : 0.05512301741232006
     }, "0.0625", "tensor(0.0754, device='cuda:0', requires_grad=True)", "ae544174", "2", "0.0625" ], [ "True", "314", "0.0625", "19.477163314819336", {
       "batch_size" : 32,
       "learning_rate" : 0.05512301741232006,
       "trial_index" : 0,
       "param/batch_size" : 32,
       "param/learning_rate" : 0.05512301741232006
     }, "0.0625", "tensor(0.0754, device='cuda:0', requires_grad=True)", "ae544174", "2", "0.0625" ] ]
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
