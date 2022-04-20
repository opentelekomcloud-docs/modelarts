.. _modelarts_03_0066:

Querying the Details About a Visualization Job
==============================================

Function
--------

This API is used to query the details about a specified visualization job based on the job name.

URI
---

GET /v1/{project_id}/visualization-jobs/{job_id}

:ref:`Table 1 <modelarts_03_0066__en-us_topic_0131202684_table569625523811>` describes the required parameters.

.. _modelarts_03_0066__en-us_topic_0131202684_table569625523811:

.. table:: **Table 1** Parameters

   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                 |
   +============+===========+========+=============================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | job_id     | Yes       | String | ID of a visualization job                                                                                                   |
   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+

Request Body
------------

None

Response Body
-------------

:ref:`Table 2 <modelarts_03_0066__en-us_topic_0131202684_table6495326155010>` describes the response parameters.

.. _modelarts_03_0066__en-us_topic_0131202684_table6495326155010:

.. table:: **Table 2** Parameters

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
   | job_name              | String                | Name of a visualization job                                                                                     |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------+
   | service_url           | String                | Endpoint of a visualization job                                                                                 |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------+
   | resource_id           | String                | Charged resource ID of a visualization job                                                                      |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------+
   | job_id                | Long                  | ID of a visualization job                                                                                       |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------+
   | job_desc              | String                | Description of a visualization job                                                                              |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------+
   | duration              | Long                  | Visualization job running duration, in milliseconds                                                             |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------+
   | create_time           | Long                  | Time when a visualization job is created, in timestamp format                                                   |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------+
   | train_url             | String                | OBS path of the visualization job output file                                                                   |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------+
   | status                | Int                   | Status of a visualization job. For details about the job statuses, see :ref:`Job Statuses <modelarts_03_0074>`. |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------+

Samples
-------

The following shows how to query the visualization job whose ID is 10.

-  Sample request

   .. code-block::

      GET https://endpoint/v1/{project_id}/visualization-jobs/10

-  Successful sample response

   .. code-block::

      {
          "duration": 33000,
          "service_url": "https://XXX/modelarts2/tensorboard/04f679b17380d32a2f32c00335c4b5ba/197/",
          "job_name": "apiTest-11",
          "create_time": 1565149736000,
          "train_url": "/wph-test/zl-test/Flowers-Set/ApiTest/",
          "job_id": 197,
          "job_desc": "ModelArts API Dialtest",
          "resource_id": "e17dd874-b5e0-4e9b-aaf0-22b045ad8571",
          "remaining_duration": null,
          "is_success": true,
          "status": 7
      }

-  Failed sample response

   .. code-block::

      {
          "is_success": false,
          "error_message": "The length of search content should be in [0,100]",
          "error_code": "ModelArts.0104"
      }

Status Code
-----------

For details about the status code, see :ref:`Table 1 <modelarts_03_0094__en-us_topic_0132773864_table1450010510213>`.
