:original_name: modelarts_03_0051.html

.. _modelarts_03_0051:

Stopping a Training Job
=======================

Function
--------

This API is used to stop a training job.

Calling this API is an asynchronous operation. The job status can be obtained by calling the APIs described in :ref:`Querying a Training Job List <modelarts_03_0046>` and :ref:`Querying the Details About a Training Job Version <modelarts_03_0047>`.

URI
---

POST /v1/{project_id}/training-jobs/{job_id}/versions/{version_id}/stop

:ref:`Table 1 <en-us_topic_0000001909907400__table38721821155840>` describes the required parameters.

.. _en-us_topic_0000001909907400__table38721821155840:

.. table:: **Table 1** Parameters

   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                               |
   +============+===========+========+===========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+
   | job_id     | Yes       | Long   | ID of a training job                                                                                                      |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+
   | version_id | Yes       | Long   | Version ID of a training job                                                                                              |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+

Request Body
------------

None

Response Body
-------------

:ref:`Table 2 <en-us_topic_0000001909907400__table61691357155927>` describes the response parameters.

.. _en-us_topic_0000001909907400__table61691357155927:

.. table:: **Table 2** Parameters

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                               |
   +=======================+=======================+===========================================================================================+
   | is_success            | Boolean               | Whether the request is successful                                                         |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------+
   | error_message         | String                | Error message of a failed API call.                                                       |
   |                       |                       |                                                                                           |
   |                       |                       | This parameter is not included when the API call succeeds.                                |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------+
   | error_code            | String                | Error code of a failed API call. For details, see :ref:`Error Codes <modelarts_03_0095>`. |
   |                       |                       |                                                                                           |
   |                       |                       | This parameter is not included when the API call succeeds.                                |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------+

Sample Request
--------------

The following shows how to stop a version of the job whose **job_id** is **10** and **version_id** is **10**.

.. code-block:: text

   POST   https://endpoint/v1/{project_id}/training-jobs/10/versions/10/stop

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
          "error_message": "Error string",
          "error_code": "ModelArts.0105"
      }

Status Code
-----------

For details about the status code, see :ref:`Status Code <modelarts_03_0094>`.
