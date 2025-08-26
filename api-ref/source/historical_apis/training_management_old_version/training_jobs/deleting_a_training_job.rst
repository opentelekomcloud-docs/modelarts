:original_name: modelarts_03_0053.html

.. _modelarts_03_0053:

Deleting a Training Job
=======================

Function
--------

This API is used to delete a training job.

Calling this API is an asynchronous operation. The job status can be obtained by calling the APIs described in :ref:`Querying a Training Job List <modelarts_03_0046>` and :ref:`Querying the Details About a Training Job Version <modelarts_03_0047>`.

URI
---

DELETE /v1/{project_id}/training-jobs/{job_id}

:ref:`Table 1 <en-us_topic_0000002340898666__table126693715562>` describes the required parameters.

.. _en-us_topic_0000002340898666__table126693715562:

.. table:: **Table 1** Parameters

   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                               |
   +============+===========+========+===========================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+
   | job_id     | Yes       | Long   | ID of a training job                                                                                                      |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+

Request Body
------------

None

Response Body
-------------

:ref:`Table 2 <en-us_topic_0000002340898666__table1221422915578>` describes the response parameters.

.. _en-us_topic_0000002340898666__table1221422915578:

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

The following shows how to delete the job whose **job_id** is **10**.

.. code-block:: text

   DELETE    https://endpoint/v1/{project_id}/training-jobs/10

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
