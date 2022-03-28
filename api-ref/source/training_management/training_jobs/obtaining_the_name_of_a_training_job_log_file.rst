Obtaining the Name of a Training Job Log File
=============================================

Function
--------

This API is used to obtain the name of a training job log file.

URI
---

GET /v1/{project_id}/training-jobs/{job_id}/versions/{version_id}/log/file-names

`Table 1 <#modelarts030054enustopic0131304290table4669394316232>`__ describes the required parameters. 

.. _modelarts030054enustopic0131304290table4669394316232:

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

`Table 2 <#modelarts030054enustopic0131304290table3969737616316>`__ describes the response parameters. 

.. _modelarts030054enustopic0131304290table3969737616316:

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
   | log_file_list         | String                | Log file name of a training job. A single-node job has only one log file, and a distributed job has multiple log files.                                                  |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Samples
-------

The following shows how to obtain the log files of the job whose **job_id** is **10** and **version_id** is **10**.

-  Sample request

   .. code-block::

      GET    https://endpoint/v1/{project_id}/training-jobs/10/versions/10/log/file-names

-  Successful sample response

   .. code-block::

      {
          "is_success": true,
          "log_file_list": [
              "teseJob.0"
          ]
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


