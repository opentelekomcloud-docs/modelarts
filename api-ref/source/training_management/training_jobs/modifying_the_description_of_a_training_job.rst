Modifying the Description of a Training Job
===========================================

Function
--------

This API is used to modify the description of a training job.

URI
---

PUT /v1/{project_id}/training-jobs/{job_id}

`Table 1 <#modelarts030052enustopic0131151011table27718806153710>`__ describes the required parameters. 

.. _modelarts030052enustopic0131151011table27718806153710:

.. table:: **Table 1** Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                                                                         |
   +============+===========+========+=====================================================================================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see `Obtaining a Project ID and Name <../../common_parameters/obtaining_a_project_id_and_name.html#modelarts030147>`__. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | job_id     | Yes       | Long   | ID of a training job                                                                                                                                                                |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Body
------------

`Table 2 <#modelarts030052enustopic0131151011table54779414153816>`__ describes the request parameters. 

.. _modelarts030052enustopic0131151011table54779414153816:

.. table:: **Table 2** Parameters

   +-----------+-----------+--------+------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                  |
   +===========+===========+========+==============================================================================+
   | job_desc  | Yes       | String | Description of a training job. The value is a string of 0 to 256 characters. |
   +-----------+-----------+--------+------------------------------------------------------------------------------+

Response Body
-------------

`Table 3 <#modelarts030052enustopic0131151011table10292351155335>`__ describes the response parameters. 

.. _modelarts030052enustopic0131151011table10292351155335:

.. table:: **Table 3** Parameters

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                              |
   +=======================+=======================+==========================================================================================================================================================================+
   | is_success            | Boolean               | Whether the request is successful.                                                                                                                                       |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | error_message         | String                | Error message of a failed API call.                                                                                                                                      |
   |                       |                       |                                                                                                                                                                          |
   |                       |                       | This parameter is not included when the API call succeeds.                                                                                                               |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | error_code            | String                | Error code of a failed API call. For details, see `Error Codes <../../common_parameters/error_codes.html>`__. This parameter is not included when the API call succeeds. |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

For details about the status code, see `Status Code <../../common_parameters/status_code.html#modelarts030094>`__.


