.. _modelarts_03_0061:

Deleting a Training Job Configuration
=====================================

Function
--------

This API is used to delete a training job configuration.

URI
---

DELETE /v1/{project_id}/training-job-configs/{config_name}

:ref:`Table 1 <modelarts_03_0061__en-us_topic_0131292965_table486226859532>` describes the required parameters.

.. _modelarts_03_0061__en-us_topic_0131292965_table486226859532:

.. table:: **Table 1** Parameter description

   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                                 |
   +=============+===========+========+=============================================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | config_name | Yes       | String | Name of a training job configuration                                                                                        |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+

Request Body
------------

None

Response Body
-------------

:ref:`Table 2 <modelarts_03_0061__en-us_topic_0131292965_table5371703815645>` describes the response parameters.

.. _modelarts_03_0061__en-us_topic_0131292965_table5371703815645:

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

For details about the status code, see :ref:`Table 1 <modelarts_03_0094__en-us_topic_0132773864_table1450010510213>`.
