:original_name: ShowAutoSearchParamsAnalysis.html

.. _ShowAutoSearchParamsAnalysis:

Obtaining the Hyperparameter Sensitivity Analysis Result
========================================================

Function
--------

This API is used to obtain the summary of hyperparameter sensitivity analysis results.

URI
---

GET /v2/{project_id}/training-jobs/{training_job_id}/autosearch-parameter-analysis

.. table:: **Table 1** Path Parameters

   +-----------------+-----------+--------+------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory | Type   | Description                                                                              |
   +=================+===========+========+==========================================================================================+
   | project_id      | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +-----------------+-----------+--------+------------------------------------------------------------------------------------------+
   | training_job_id | Yes       | String | ID of a training job.                                                                    |
   +-----------------+-----------+--------+------------------------------------------------------------------------------------------+

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

The following shows how to query the hyperparameter sensitivity analysis result of the job whose **training_job_id** is **04f679b17380d32a2f32c00335c4b5ba**.

.. code-block:: text

   GET https://endpoint/v2/{project_id}/training-jobs/04f679b17380d32a2f32c00335c4b5ba/autosearch-parameter-analysis

Example Responses
-----------------

**Status code: 200**

ok

.. code-block::

   {
     "header" : [ "parameters", "the mean/std of importance" ],
     "data" : [ [ "batch_size", "0.2443/0.3867" ], [ "learning_rate", "0.6992/0.4040" ] ]
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
