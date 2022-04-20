.. _modelarts_03_0048:

Deleting a Version of a Training Job
====================================

Function
--------

This API is used to delete a version of a training job.

Calling this API is an asynchronous operation. The job status can be obtained by calling the APIs described in :ref:`Querying a Training Job List <modelarts_03_0046>` and :ref:`Querying the Details About a Training Job Version <modelarts_03_0047>`.

URI
---

DELETE /v1/{project_id}/training-jobs/{job_id}/versions/{version_id}

:ref:`Table 1 <modelarts_03_0048__en-us_topic_0131151009_table126693715562>` describes the required parameters.

.. _modelarts_03_0048__en-us_topic_0131151009_table126693715562:

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

:ref:`Table 2 <modelarts_03_0048__en-us_topic_0131151009_table1221422915578>` describes the response parameters.

.. _modelarts_03_0048__en-us_topic_0131151009_table1221422915578:

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

Samples
-------

-  Sample request

   .. code-block::

      DELETE    https://endpoint/v1/{project_id}/training-jobs/10/versions/10

-  Successful sample response

   .. code-block::

      {
          "is_success": true
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
