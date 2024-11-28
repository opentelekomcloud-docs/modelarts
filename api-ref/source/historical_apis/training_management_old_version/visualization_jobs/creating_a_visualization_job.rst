:original_name: modelarts_03_0064.html

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

:ref:`Table 1 <en-us_topic_0000001909907520__table569625523811>` describes the required parameters.

.. _en-us_topic_0000001909907520__table569625523811:

.. table:: **Table 1** Parameters

   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                               |
   +============+===========+========+===========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+

Request Body
------------

:ref:`Table 2 <en-us_topic_0000001909907520__table196759327241>` describes the request parameters.

.. _en-us_topic_0000001909907520__table196759327241:

.. table:: **Table 2** Parameters

   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                                                                     |
   +===========+===========+========+=================================================================================================================================================================================+
   | job_name  | Yes       | String | Name of a visualization job. The value must contain 1 to 20 characters consisting of only digits, letters, underscores (_), and hyphens (-).                                    |
   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | job_desc  | No        | String | Description of a visualization job. The value must contain 0 to 256 characters. By default, this parameter is left blank.                                                       |
   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | train_url | Yes       | String | OBS path                                                                                                                                                                        |
   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | job_type  | No        | String | Type of a visualization job. You can create visualization jobs of TensorBoard and MindInsight types. The default type is TensorBoard.                                           |
   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | flavor    | No        | Object | Specifications when a visualization job is created. You do not need to set this parameter. For details, see :ref:`Table 3 <en-us_topic_0000001909907520__table18319659123214>`. |
   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | schedule  | No        | Object | Auto stop setting. For details, see :ref:`Table 4 <en-us_topic_0000001909907520__table3694202918279>`.                                                                          |
   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000001909907520__table18319659123214:

.. table:: **Table 3** **flavor** parameters

   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                   |
   +===========+===========+========+===============================================================================================================+
   | code      | Yes       | String | Resource specification code of a visualization job. You can obtain the code through the **flavor** parameter. |
   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000001909907520__table3694202918279:

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

:ref:`Table 5 <en-us_topic_0000001909907520__table28681002612>` describes the response parameters.

.. _en-us_topic_0000001909907520__table28681002612:

.. table:: **Table 5** Parameters

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                     |
   +=======================+=======================+=================================================================================================================+
   | is_success            | Boolean               | Whether the request is successful                                                                               |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------+
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

Sample Request
--------------

The following shows how to create a visualization job whose name is **visualization-job**, description is **this is a visualization job**, and OBS path is **/obs/name/**.

.. code-block:: text

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

Sample Response
---------------

-  Successful response

   .. code-block::

      {
          "is_success": true,
          "job_id": "10",
          "job_name": "visualization-job",
          "status": "1",
          "create_time": "1524189990635"
      }

-  Failed response

   .. code-block::

      {
          "is_success": false,
          "error_message": "error message",
          "error_code": "ModelArts.0103"
      }

Status Code
-----------

For details about the status code, see :ref:`Table 1 <en-us_topic_0000001909907492__table1450010510213>`.
