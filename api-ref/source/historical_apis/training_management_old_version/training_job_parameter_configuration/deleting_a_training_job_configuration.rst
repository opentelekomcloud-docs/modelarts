:original_name: modelarts_03_0061.html

.. _modelarts_03_0061:

Deleting a Training Job Configuration
=====================================

Function
--------

This API is used to delete a training job configuration.

URI
---

DELETE /v1/{project_id}/training-job-configs/{config_name}

:ref:`Table 1 <en-us_topic_0000002233928732__table486226859532>` describes the required parameters.

.. _en-us_topic_0000002233928732__table486226859532:

.. table:: **Table 1** Parameters

   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                               |
   +=============+===========+========+===========================================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+
   | config_name | Yes       | String | Name of a training job configuration                                                                                      |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+

Request Body
------------

None

Response Body
-------------

:ref:`Table 2 <en-us_topic_0000002233928732__table5371703815645>` describes the response parameters.

.. _en-us_topic_0000002233928732__table5371703815645:

.. table:: **Table 2** Parameters

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

Sample Request
--------------

The following shows how to delete the job configuration named **test-trainconfig**.

.. code-block:: text

   DELETE    https://endpoint/v1/{project_id}/training-job-configs/test-trainconfig

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

For details about the status code, see :ref:`Table 1 <en-us_topic_0000002268848277__table1450010510213>`.
