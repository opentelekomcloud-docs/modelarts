:original_name: modelarts_03_0069.html

.. _modelarts_03_0069:

Stopping a Visualization Job
============================

Function
--------

This API is used to stop a visualization job. Calling this API is an asynchronous operation. The job status can be obtained by calling the APIs described in :ref:`Querying a Visualization Job List <modelarts_03_0065>` and :ref:`Querying the Details About a Visualization Job <modelarts_03_0066>`.

URI
---

POST /v1/{project_id}/visualization-jobs/{job_id}/stop

:ref:`Table 1 <en-us_topic_0000001909747468__table20736351173356>` describes the required parameters.

.. _en-us_topic_0000001909747468__table20736351173356:

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

:ref:`Table 2 <en-us_topic_0000001909747468__table47616479111324>` describes the response parameters.

.. _en-us_topic_0000001909747468__table47616479111324:

.. table:: **Table 2** Parameters

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                               |
   +=======================+=======================+===========================================================================================+
   | is_success            | Boolean               | Whether the request is successful                                                         |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------+
   | error_code            | String                | Error code of a failed API call. For details, see :ref:`Error Codes <modelarts_03_0095>`. |
   |                       |                       |                                                                                           |
   |                       |                       | This parameter is not included when the API call succeeds.                                |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------+
   | error_message         | String                | Error message of a failed API call.                                                       |
   |                       |                       |                                                                                           |
   |                       |                       | This parameter is not included when the API call succeeds.                                |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------+

Sample Request
--------------

The following shows how to stop the visualization job whose ID is 10.

.. code-block:: text

   POST    https://endpoint/v1/{project_id}/visualization-jobs/10/stop

Sample Response
---------------

-  Successful response

   .. code-block::

      {
          "is_success": true
      }

-  Failed response

   .. code-block::

      {
          "is_success": false,
          "error_message": "This job can't be stop. job status: 10",
          "error_code": "ModelArts.0105"
      }

Status Code
-----------

For details about the status code, see :ref:`Table 1 <en-us_topic_0000001909907492__table1450010510213>`.
