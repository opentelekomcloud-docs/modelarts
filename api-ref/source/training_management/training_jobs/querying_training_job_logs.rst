.. _modelarts_03_0149:

Querying Training Job Logs
==========================

Function
--------

This API is used to query detailed information about training job logs by row.

URI
---

GET /v1/{project_id}/training-jobs/{job_id}/versions/{version_id}/aom-log

:ref:`Table 1 <modelarts_03_0149__en-us_topic_0188093645_table4442765616454>` describes the required parameters.

.. _modelarts_03_0149__en-us_topic_0188093645_table4442765616454:

.. table:: **Table 1** Parameters

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

:ref:`Table 2 <modelarts_03_0149__en-us_topic_0188093645_table87520312215>` describes the request parameters.

.. _modelarts_03_0149__en-us_topic_0188093645_table87520312215:

.. table:: **Table 2** Parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                         |
   +=================+=================+=================+=====================================================================================================================================================================+
   | base_line       | No              | String          | Base line of the log, which is obtained from an API response. If the value is empty, the latest log is obtained.                                                    |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | lines           | No              | Integer         | Length of the obtained log. The default value is 50 lines. The value range is [0, 500].                                                                             |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_file        | Yes             | String          | Name of the log file to be viewed. For details about how to obtain the log file name, see :ref:`Obtaining the Name of a Training Job Log File <modelarts_03_0054>`. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | order           | No              | String          | Log query direction                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                     |
   |                 |                 |                 | -  desc: Querying next records                                                                                                                                      |
   |                 |                 |                 | -  asc: Querying previous records                                                                                                                                   |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Body
-------------

:ref:`Table 3 <modelarts_03_0149__en-us_topic_0188093645_table1414514116749>` describes the response parameters.

.. _modelarts_03_0149__en-us_topic_0188093645_table1414514116749:

.. table:: **Table 3** Parameters

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                               |
   +=======================+=======================+===========================================================================================+
   | error_message         | String                | Error message of a failed API call.                                                       |
   |                       |                       |                                                                                           |
   |                       |                       | This parameter is not included when the API call succeeds.                                |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------+
   | error_code            | String                | Error code of a failed API call. For details, see :ref:`Error Codes <modelarts_03_0095>`. |
   |                       |                       |                                                                                           |
   |                       |                       | This parameter is not included when the API call succeeds.                                |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------+
   | content               | String                | Content of the requested log                                                              |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------+
   | lines                 | Integer               | Lines of the obtained logs                                                                |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------+
   | start_line            | String                | Start position of the obtained log                                                        |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------+
   | end_line              | String                | End position of the obtained log                                                          |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------+
   | is_success            | Boolean               | Whether the request is successful                                                         |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------+

Samples
-------

The following shows how to query the logs contained in **log1.log** of the job whose **job_id** is **10** and **version_id** is **10**.

-  Sample request

   .. code-block::

      GET    https://endpoint/v1/{project_id}/training-jobs/10/versions/10/aom-log?log_file=log1.log&base_line= 1551252759254000002&lines=50&order=desc

-  Successful sample response

   .. code-block::

      {
          "is_success": true,
          "start_line":1551252759254000002,
          "content": "Log string",
          "end_line": "1551252759254000003",
          "lines": "1"
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
