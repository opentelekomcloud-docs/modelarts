Deleting a Training Job Configuration
=====================================

Function
--------

This API is used to delete a training job configuration.

URI
---

DELETE /v1/{project_id}/training-job-configs/{config_name}

`Table 1 <#modelarts030061enustopic0131292965table486226859532>`__ describes the required parameters. 

.. _modelarts030061enustopic0131292965table486226859532:

.. table:: **Table 1** Parameter description

   +-------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                                                                                         |
   +=============+===========+========+=====================================================================================================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain the project ID, see `Obtaining a Project ID and Name <../../common_parameters/obtaining_a_project_id_and_name.html#modelarts030147>`__. |
   +-------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | config_name | Yes       | String | Name of a training job configuration                                                                                                                                                |
   +-------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Body
------------

None

Response Body
-------------

`Table 2 <#modelarts030061enustopic0131292965table5371703815645>`__ describes the response parameters.



.. _modelarts030061enustopic0131292965table5371703815645:

.. table:: **Table 2** Parameter description

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                              |
   +=======================+=======================+==========================================================================================================================================================================+
   | is_success            | Boolean               | Whether the request is successful                                                                                                                                        |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | error_message         | String                | Error message of a failed API call.                                                                                                                                      |
   |                       |                       |                                                                                                                                                                          |
   |                       |                       | This parameter is not included when the API call succeeds.                                                                                                               |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | error_code            | String                | Error code of a failed API call. For details, see `Error Codes <../../common_parameters/error_codes.html>`__. This parameter is not included when the API call succeeds. |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Samples
-------

The following shows how to delete the job configuration named **test-trainconfig**.

-  Sample request

   .. code-block::

      DELETE    https://endpoint/v1/{project_id}/training-job-configs/test-trainconfig

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

For details about the status code, see `Table 1 <../../common_parameters/status_code.html#modelarts030094enustopic0132773864table1450010510213>`__.


