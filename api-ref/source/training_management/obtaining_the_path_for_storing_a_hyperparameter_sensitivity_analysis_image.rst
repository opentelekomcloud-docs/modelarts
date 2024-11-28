:original_name: ShowAutoSearchParamAnalysisResultPath.html

.. _ShowAutoSearchParamAnalysisResultPath:

Obtaining the Path for Storing a Hyperparameter Sensitivity Analysis Image
==========================================================================

Function
--------

This API is used to obtain the path for storing a hyperparameter sensitivity analysis image.

URI
---

GET /v2/{project_id}/training-jobs/{training_job_id}/autosearch-parameter-analysis/{parameter_name}

.. table:: **Table 1** Path Parameters

   +-----------------+-----------+--------+------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory | Type   | Description                                                                              |
   +=================+===========+========+==========================================================================================+
   | parameter_name  | Yes       | String | Name of the search parameter.                                                            |
   +-----------------+-----------+--------+------------------------------------------------------------------------------------------+
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

   +-----------+--------+--------------------------------------------------------------+
   | Parameter | Type   | Description                                                  |
   +===========+========+==============================================================+
   | file_path | String | Path for storing hyperparameter sensitivity analysis images. |
   +-----------+--------+--------------------------------------------------------------+

Example Requests
----------------

The following shows how to query the path for storing the sensitivity analysis image of hyperparameter **batch_size** in the yperparameter sensitivity analysis results of the job whose **training_job_id** is **e346206c-6fde-4c33-9dcd-55be17858ceb**.

.. code-block:: text

   GET https://endpoint/v2/{project_id}/training-jobs/e346206c-6fde-4c33-9dcd-55be17858ceb/autosearch-parameter-analysis/batch_size

Example Responses
-----------------

**Status code: 200**

ok

.. code-block::

   {
     "file_path" : "/test-wrk/autosearch-test/output/log/hyperparameter-analysis/fanova/batch_size.png"
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
