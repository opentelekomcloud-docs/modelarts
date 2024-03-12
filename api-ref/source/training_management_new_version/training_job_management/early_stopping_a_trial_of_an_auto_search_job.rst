:original_name: ShowAutoSearchTrialEarlyStop.html

.. _ShowAutoSearchTrialEarlyStop:

Early Stopping a Trial of an Auto Search Job
============================================

Function
--------

This API is used to early stop a trial of an auto search job.

URI
---

POST /v2/{project_id}/training-jobs/{training_job_id}/autosearch-trial-earlystop/{trial_id}

.. table:: **Table 1** Path Parameters

   +-----------------+-----------+--------+---------------------------------------------------------------------------------+
   | Parameter       | Mandatory | Type   | Description                                                                     |
   +=================+===========+========+=================================================================================+
   | project_id      | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID <modelarts_03_0147>`. |
   +-----------------+-----------+--------+---------------------------------------------------------------------------------+
   | training_job_id | Yes       | String | ID of a training job.                                                           |
   +-----------------+-----------+--------+---------------------------------------------------------------------------------+
   | trial_id        | Yes       | String | **trial_id** for hyperparameter search.                                         |
   +-----------------+-----------+--------+---------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   =============== ====== ================================================
   Parameter       Type   Description
   =============== ====== ================================================
   earlystop_trial String **trial_id** of the trial that is early stopped.
   =============== ====== ================================================

Example Requests
----------------

The following shows how to early stop the trial whose **trial_id** is **50093e6c** using the job whose **training_job_id** is **e346206c-6fde-4c33-9dcd-55be17858ceb** as an example.

.. code-block:: text

   POST https://endpoint/v2/{project_id}/training-jobs/e346206c-6fde-4c33-9dcd-55be17858ceb/autosearch-trial-earlystop/50093e6c

Example Responses
-----------------

**Status code: 200**

ok

.. code-block::

   {
     "earlystop_trial" : "50093e6c"
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
