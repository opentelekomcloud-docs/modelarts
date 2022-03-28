Restarting a Visualization Job
==============================

Function
--------

This API is used to restart a visualization job. Calling this API is an asynchronous operation. The job status can be obtained by calling the APIs described in `Querying a Visualization Job List <../../training_management/visualization_jobs/querying_a_visualization_job_list.html#modelarts030065>`__ and `Querying the Details About a Visualization Job <../../training_management/visualization_jobs/querying_the_details_about_a_visualization_job.html#modelarts030066>`__.

URI
---

POST /v1/{project_id}/visualization-jobs/{job_id}/restart

`Table 1 <#modelarts030070enustopic0131202688table20736351173356>`__ describes the required parameters. 

.. _modelarts030070enustopic0131202688table20736351173356:

.. table:: **Table 1** Parameter description

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                                                                         |
   +============+===========+========+=====================================================================================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see `Obtaining a Project ID and Name <../../common_parameters/obtaining_a_project_id_and_name.html#modelarts030147>`__. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | job_id     | Yes       | String | ID of a visualization job                                                                                                                                                           |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Body
------------

None

Response Body
-------------

`Table 2 <#modelarts030070enustopic0131202688table1616937211145>`__ describes the response parameters. 

.. _modelarts030070enustopic0131202688table1616937211145:

.. table:: **Table 2** Parameter description

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                   |
   +=======================+=======================+===============================================================================================================+
   | is_success            | Boolean               | Whether the request is successful                                                                             |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------+
   | error_code            | String                | Error code of a failed API call. For details, see `Error Codes <../../common_parameters/error_codes.html>`__. |
   |                       |                       |                                                                                                               |
   |                       |                       | This parameter is not included when the API call succeeds.                                                    |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------+
   | error_message         | String                | Error message of a failed API call.                                                                           |
   |                       |                       |                                                                                                               |
   |                       |                       | This parameter is not included when the API call succeeds.                                                    |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------+

Samples
-------

The following shows how to restart the visualization job whose ID is 10.

-  Sample request

   .. code-block::

      POST    https://endpoint/v1/{project_id}/visualization-jobs/10/restart

-  Successful sample response

   .. code-block::

      {
          "is_success": true
      }

-  Failed sample response

   .. code-block::

      {
          "is_success": false,
          "error_message": "This job can't be resubmit. job status: 8",
          "error_code": "ModelArts.0105"
      }

Status Code
-----------

For details about the status code, see `Table 1 <../../common_parameters/status_code.html#modelarts030094enustopic0132773864table1450010510213>`__.


