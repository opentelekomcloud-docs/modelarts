:original_name: DeleteTrainingJob.html

.. _DeleteTrainingJob:

Deleting a Training Job
=======================

Function
--------

This API is used to delete a training job.

URI
---

DELETE /v2/{project_id}/training-jobs/{training_job_id}

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

None

Example Requests
----------------

The following shows how to delete a training job whose UUID is **3faf5c03-aaa1-4cbe-879d-24b05d997347**.

.. code-block:: text

   DELETE https://endpoint/v2/{project_id}/training-jobs/3faf5c03-aaa1-4cbe-879d-24b05d997347

Example Responses
-----------------

**Status code: 202**

No Content

.. code-block::

   ""

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
202         No Content
=========== ===========

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
