.. _modelarts_03_0064:

Creating a Visualization Job
============================

Function
--------

This API is used to create a visualization job.

Calling this API is an asynchronous operation. The job status can be obtained by calling the APIs described in :ref:`Querying a Visualization Job List <modelarts_03_0065>` and :ref:`Querying the Details About a Visualization Job <modelarts_03_0066>`.

URI
---

POST /v1/{project_id}/visualization-jobs

:ref:`Table 1 <modelarts_03_0064__en-us_topic_0131202682_table569625523811>` describes the required parameters.

.. _modelarts_03_0064__en-us_topic_0131202682_table569625523811:

.. table:: **Table 1** Parameters

   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                 |
   +============+===========+========+=============================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+

Request Body
------------

:ref:`Table 2 <modelarts_03_0064__en-us_topic_0131202682_table196759327241>` describes the request parameters.

.. _modelarts_03_0064__en-us_topic_0131202682_table196759327241:

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

.. table:: **Table 3** **flavor** parameters

   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                   |
   +===========+===========+========+===============================================================================================================+
   | code      | Yes       | String | Resource specification code of a visualization job. You can obtain the code through the **flavor** parameter. |
   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------+

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

:ref:`Table 5 <modelarts_03_0064__en-us_topic_0131202682_table28681002612>` describes the response parameters.

.. _modelarts_03_0064__en-us_topic_0131202682_table28681002612:

.. table:: **Table 5** Parameters

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                     |
   +=======================+=======================+=================================================================================================================+
   | error_message         | String                | Error message of a failed API call.                                                                             |
   |                       |                       |                                                                                                                 |
   |                       |                       | This parameter is not included when the API call succeeds.                                                      |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------+
   | error_code            | String                | Error code of a failed API call. For details, see :ref:`Error Codes <modelarts_03_0095>`.                       |
   |                       |                       |                                                                                                                 |
   |                       |                       | This parameter is not included when the API call succeeds.                                                      |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------+
   | job_id                | Long                  | ID of a visualization job                                                                                       |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------+
   | job_name              | String                | Name of a visualization job                                                                                     |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------+
   | status                | Integer               | Status of a visualization job. For details about the job statuses, see :ref:`Job Statuses <modelarts_03_0074>`. |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------+
   | create_time           | Long                  | Time when a visualization job is created, in timestamp format                                                   |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------+
   | service_url           | String                | Endpoint of a visualization job                                                                                 |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------+

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

For details about the status code, see :ref:`Table 1 <modelarts_03_0094__en-us_topic_0132773864_table1450010510213>`.
