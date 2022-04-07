.. _modelarts_03_0054:

Obtaining the Name of a Training Job Log File
=============================================

Function
--------

This API is used to obtain the name of a training job log file.

URI
---

GET /v1/{project_id}/training-jobs/{job_id}/versions/{version_id}/log/file-names

:ref:`Table 1 <modelarts_03_0054__en-us_topic_0131304290_table4669394316232>` describes the required parameters.

.. _modelarts_03_0054__en-us_topic_0131304290_table4669394316232:

.. table:: **Table 1** Parameter description

   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                 |
   +============+===========+========+=============================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | job_id     | Yes       | Long   | ID of a training job                                                                                                        |
   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | version_id | Yes       | Long   | Version ID of a training job                                                                                                |
   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+

Request Body
------------

None

Response Body
-------------

:ref:`Table 2 <modelarts_03_0054__en-us_topic_0131304290_table3969737616316>` describes the response parameters.

.. _modelarts_03_0054__en-us_topic_0131304290_table3969737616316:

.. table:: **Table 2** Parameter description

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                          |
   +=======================+=======================+======================================================================================================================================================+
   | is_success            | Boolean               | Whether the request is successful                                                                                                                    |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | error_message         | String                | Error message of a failed API call.                                                                                                                  |
   |                       |                       |                                                                                                                                                      |
   |                       |                       | This parameter is not included when the API call succeeds.                                                                                           |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | error_code            | String                | Error code of a failed API call. For details, see :ref:`Error Codes <modelarts_03_0095>`. This parameter is not included when the API call succeeds. |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_file_list         | String                | Log file name of a training job. A single-node job has only one log file, and a distributed job has multiple log files.                              |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+

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

For details about the status code, see :ref:`Status Code <modelarts_03_0094>`.
