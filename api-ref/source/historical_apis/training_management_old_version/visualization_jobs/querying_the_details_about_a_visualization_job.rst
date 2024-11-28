:original_name: modelarts_03_0066.html

.. _modelarts_03_0066:

Querying the Details About a Visualization Job
==============================================

Function
--------

This API is used to obtain the details about a specified visualization job based on the job name.

URI
---

GET /v1/{project_id}/visualization-jobs/{job_id}

:ref:`Table 1 <en-us_topic_0000001909747500__table569625523811>` describes the required parameters.

.. _en-us_topic_0000001909747500__table569625523811:

.. table:: **Table 1** Parameters

   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                               |
   +============+===========+========+===========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+
   | job_id     | Yes       | String | ID of a visualization job                                                                                                 |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+

Request Body
------------

None

Response Body
-------------

:ref:`Table 2 <en-us_topic_0000001909747500__table6495326155010>` describes the response parameters.

.. _en-us_topic_0000001909747500__table6495326155010:

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

Sample Request
--------------

The following shows how to obtain the visualization job whose ID is 10.

.. code-block:: text

   GET https://endpoint/v1/{project_id}/visualization-jobs/10

Sample Response
---------------

-  Successful response

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
          "status": 7
      }

-  Failed response

   .. code-block::

      {
          "error_message": "The length of search content should be in [0,100]",
          "error_code": "ModelArts.0104"
      }

Status Code
-----------

For details about the status code, see :ref:`Table 1 <en-us_topic_0000001909907492__table1450010510213>`.
