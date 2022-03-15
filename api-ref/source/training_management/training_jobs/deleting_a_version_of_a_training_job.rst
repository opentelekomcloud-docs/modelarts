Deleting a Version of a Training Job
====================================

Function
--------

This API is used to delete a version of a training job.

Calling this API is an asynchronous operation. The job status can be obtained by calling the APIs described in `Querying a Training Job List <../../training_management/training_jobs/querying_a_training_job_list.html#modelarts030046>`__ and `Querying the Details About a Training Job Version <../../training_management/training_jobs/querying_the_details_about_a_training_job_version.html#modelarts030047>`__.

URI
---

DELETE /v1/{project_id}/training-jobs/{job_id}/versions/{version_id}

`Table 1 <#modelarts030048enustopic0131151009table126693715562>`__ describes the required parameters. 

.. _modelarts030048enustopic0131151009table126693715562:

.. table:: **Table 1** Parameter description

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                                                                         |
   +============+===========+========+=====================================================================================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see `Obtaining a Project ID and Name <../../common_parameters/obtaining_a_project_id_and_name.html#modelarts030147>`__. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | job_id     | Yes       | Long   | ID of a training job                                                                                                                                                                |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version_id | Yes       | Long   | Version ID of a training job                                                                                                                                                        |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Body
------------

None

Response Body
-------------

`Table 2 <#modelarts030048enustopic0131151009table1221422915578>`__ describes the response parameters. 

.. _modelarts030048enustopic0131151009table1221422915578:

.. table:: **Table 2** Parameter description

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                              |
   +=======================+=======================+==========================================================================================================================================================================+
   | is_success            | Boolean               | Whether the request is successful                                                                                                                                        |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | error_message         | String                | Error message of a failed API call.                                                                                                                                      |
   |                       |                       |                                                                                                                                                                          |
   |                       |                       | This parameter is not included when the API call succeeds.                                                                                                               |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | error_code            | String                | Error code of a failed API call. For details, see `Error Codes <../../common_parameters/error_codes.html>`__. This parameter is not included when the API call succeeds. |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Samples
-------

-  Sample request

   .. code-block::

      DELETE    https://endpoint/v1/{project_id}/training-jobs/10/versions/10

-  Successful sample response

   .. code-block::

      {
          "is_success": true
      }

-  Failed sample response

   .. code-block::

      {
          "is_success": false,
          "error_message": "Error string",
          "error_code": "ModelArts.0105"
      }

Status Code
-----------

For details about the status code, see `Status Code <../../common_parameters/status_code.html#modelarts030094>`__.

