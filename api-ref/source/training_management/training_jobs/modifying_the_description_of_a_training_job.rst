.. _modelarts_03_0052:

Modifying the Description of a Training Job
===========================================

Function
--------

This API is used to modify the description of a training job.

URI
---

PUT /v1/{project_id}/training-jobs/{job_id}

:ref:`Table 1 <modelarts_03_0052__en-us_topic_0131151011_table27718806153710>` describes the required parameters.

.. _modelarts_03_0052__en-us_topic_0131151011_table27718806153710:

.. table:: **Table 1** Parameters

   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                 |
   +============+===========+========+=============================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | job_id     | Yes       | Long   | ID of a training job                                                                                                        |
   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+

Request Body
------------

:ref:`Table 2 <modelarts_03_0052__en-us_topic_0131151011_table54779414153816>` describes the request parameters.

.. _modelarts_03_0052__en-us_topic_0131151011_table54779414153816:

.. table:: **Table 2** Parameters

   +-----------+-----------+--------+------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                  |
   +===========+===========+========+==============================================================================+
   | job_desc  | Yes       | String | Description of a training job. The value is a string of 0 to 256 characters. |
   +-----------+-----------+--------+------------------------------------------------------------------------------+

Response Body
-------------

:ref:`Table 3 <modelarts_03_0052__en-us_topic_0131151011_table10292351155335>` describes the response parameters.

.. _modelarts_03_0052__en-us_topic_0131151011_table10292351155335:

.. table:: **Table 3** Parameters

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                          |
   +=======================+=======================+======================================================================================================================================================+
   | is_success            | Boolean               | Whether the request is successful.                                                                                                                   |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | error_message         | String                | Error message of a failed API call.                                                                                                                  |
   |                       |                       |                                                                                                                                                      |
   |                       |                       | This parameter is not included when the API call succeeds.                                                                                           |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | error_code            | String                | Error code of a failed API call. For details, see :ref:`Error Codes <modelarts_03_0095>`. This parameter is not included when the API call succeeds. |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+

Samples
-------

The following shows how to modify the description of the job whose **job_id** is **10**.

-  Sample request

   .. code-block::

      PUT    https://endpoint/v1/{project_id}/training-jobs/10
      {
          "job_desc": "This is a ModelArts job"
      }

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
