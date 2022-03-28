Creating a Visualization Job
============================

Function
--------

This API is used to create a visualization job.

Calling this API is an asynchronous operation. The job status can be obtained by calling the APIs described in `Querying a Visualization Job List <../../training_management/visualization_jobs/querying_a_visualization_job_list.html#modelarts030065>`__ and `Querying the Details About a Visualization Job <../../training_management/visualization_jobs/querying_the_details_about_a_visualization_job.html#modelarts030066>`__.

URI
---

POST /v1/{project_id}/visualization-jobs

`Table 1 <#modelarts030064enustopic0131202682table569625523811>`__ describes the required parameters. 

.. _modelarts030064enustopic0131202682table569625523811:

.. table:: **Table 1** Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                                                                         |
   +============+===========+========+=====================================================================================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see `Obtaining a Project ID and Name <../../common_parameters/obtaining_a_project_id_and_name.html#modelarts030147>`__. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Body
------------

`Table 2 <#modelarts030064enustopic0131202682table196759327241>`__ describes the request parameters.



.. _modelarts030064enustopic0131202682table196759327241:

.. table:: **Table 2** Parameters

   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                                    |
   +===========+===========+========+================================================================================================================================================+
   | job_name  | Yes       | String | Name of a visualization job. The value is a string of 1 to 20 characters consisting of only digits, letters, underscores (_), and hyphens (-). |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | job_desc  | No        | String | Description of a visualization job. The value is a string of 0 to 256 characters. By default, this parameter is left blank.                    |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | train_url | Yes       | String | OBS path                                                                                                                                       |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | job_type  | No        | String | Type of a visualization job. You can create visualization jobs of TensorBoard and MindInsight types. The default type is TensorBoard.          |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | flavor    | No        | JSON   | Specifications when a visualization job is created. You do not need to set this parameter.                                                     |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | schedule  | No        | JSON   | Automatic stop setting                                                                                                                         |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------+



.. _modelarts030064enustopic0131202682table18319659123214:

.. table:: **Table 3** **flavor** parameters

   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                   |
   +===========+===========+========+===============================================================================================================+
   | code      | Yes       | String | Resource specification code of a visualization job. You can obtain the code through the **flavor** parameter. |
   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------+



.. _modelarts030064enustopic0131202682table3694202918279:

.. table:: **Table 4** **schedule** parameters

   +-----------+-----------+--------+-----------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                         |
   +===========+===========+========+=====================================================+
   | type      | Yes       | String | Set this parameter to **stop**.                     |
   +-----------+-----------+--------+-----------------------------------------------------+
   | time_unit | Yes       | String | Unit of auto stop duration. The value is **HOURS**. |
   +-----------+-----------+--------+-----------------------------------------------------+
   | duration  | Yes       | Int    | Auto stop duration. The value ranges from 0 to 24.  |
   +-----------+-----------+--------+-----------------------------------------------------+

Response Body
-------------

`Table 5 <#modelarts030064enustopic0131202682table28681002612>`__ describes the response parameters.



.. _modelarts030064enustopic0131202682table28681002612:

.. table:: **Table 5** Parameters

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                            |
   +=======================+=======================+========================================================================================================================================================+
   | error_message         | String                | Error message of a failed API call.                                                                                                                    |
   |                       |                       |                                                                                                                                                        |
   |                       |                       | This parameter is not included when the API call succeeds.                                                                                             |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | error_code            | String                | Error code of a failed API call. For details, see `Error Codes <../../common_parameters/error_codes.html>`__.                                          |
   |                       |                       |                                                                                                                                                        |
   |                       |                       | This parameter is not included when the API call succeeds.                                                                                             |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | job_id                | Long                  | ID of a visualization job                                                                                                                              |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | job_name              | String                | Name of a visualization job                                                                                                                            |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                | Integer               | Status of a visualization job. For details about the job statuses, see `Job Statuses <../../training_management/job_statuses.html#modelarts030074>`__. |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time           | Long                  | Time when a visualization job is created, in timestamp format                                                                                          |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | service_url           | String                | Endpoint of a visualization job                                                                                                                        |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+

Samples
-------

The following shows how to create a visualization job whose name is **visualization-job**, description is **this is a visualization job**, and OBS path is **/obs/name/**.

-  Sample request

   .. code-block::

      POST  https://endpoint/v1/{project_id}/visualization-jobs
      {
          "job_name": "visualization-job",
          "job_desc": "this is a visualization job",
          "train_url": "/obs/name/",
          "job_type": "mindinsight",
          "schedule": [
              {
                  "type": "stop",
                  "time_unit": "HOURS",
                  "duration": 1
              }
          ]
      }

-  Successful sample response

   .. code-block::

      {
          "is_success": true,
          "job_id": "10",
          "job_name": "visualization-job",
          "status": "1",
          "create_time": "1524189990635"
      }

-  Failed sample response

   .. code-block::

      {
          "is_success": false,
          "error_message": "error message",
          "error_code": "ModelArts.0103"
      }

Status Code
-----------

For details about the status code, see `Table 1 <../../common_parameters/status_code.html#modelarts030094enustopic0132773864table1450010510213>`__.


