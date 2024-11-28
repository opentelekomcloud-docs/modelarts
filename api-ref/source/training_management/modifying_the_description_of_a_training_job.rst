:original_name: ChangeTrainingJobDescription.html

.. _ChangeTrainingJobDescription:

Modifying the Description of a Training Job
===========================================

Function
--------

This API is used to modify the description of a training job.

URI
---

PUT /v2/{project_id}/training-jobs/{training_job_id}

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

.. table:: **Table 2** Request body parameters

   +-------------+-----------+--------+-------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                     |
   +=============+===========+========+=================================================================================================+
   | description | No        | String | Training job description, which consists of 0 to 256 characters. The default value is **NULL**. |
   +-------------+-----------+--------+-------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Requests
----------------

The following shows how to modify a training job with UUID **3faf5c03-aaa1-4cbe-879d-24b05d997347**. After the modification, call the API for obtaining a training job(ListTrainingJobs.xml) to view the modified description.

.. code-block:: text

   PUT https://endpoint/v2/{project_id}/training-jobs/3faf5c03-aaa1-4cbe-879d-24b05d997347

   {
     "description" : "hahaha"
   }

Example Responses
-----------------

**Status code: 200**

No Content

.. code-block::

   null

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
200         No Content
=========== ===========

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
