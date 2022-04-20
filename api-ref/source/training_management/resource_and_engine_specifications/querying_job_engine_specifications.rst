.. _modelarts_03_0073:

Querying Job Engine Specifications
==================================

Function
--------

This API is used to query the engine type and version of a specified job.

You must specify the engine specifications when creating a training job or an inference job.

URI
---

GET /v1/{project_id}/job/ai-engines

:ref:`Table 1 <modelarts_03_0073__en-us_topic_0131307648_table6017292495443>` describes the required parameters.

.. _modelarts_03_0073__en-us_topic_0131307648_table6017292495443:

.. table:: **Table 1** Parameters

   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                 |
   +============+===========+========+=============================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Parameters

   +-----------+-----------+--------+--------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                            |
   +===========+===========+========+========================================================+
   | job_type  | No        | String | Job type. The value can be **train** or **inference**. |
   +-----------+-----------+--------+--------------------------------------------------------+

Request Body
------------

None

Response Body
-------------

:ref:`Table 3 <modelarts_03_0073__en-us_topic_0131307648_table41713500151328>` describes the response parameters.

.. _modelarts_03_0073__en-us_topic_0131307648_table41713500151328:

.. table:: **Table 3** Parameters

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                |
   +=======================+=======================+============================================================================================================================================+
   | is_success            | Boolean               | Whether the request is successful                                                                                                          |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | error_message         | String                | Error message of a failed API call.                                                                                                        |
   |                       |                       |                                                                                                                                            |
   |                       |                       | This parameter is not included when the API call succeeds.                                                                                 |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | error_code            | String                | Error code of a failed API call. For details, see :ref:`Error Codes <modelarts_03_0095>`.                                                  |
   |                       |                       |                                                                                                                                            |
   |                       |                       | This parameter is not included when the API call succeeds.                                                                                 |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | engines               | **engines** array     | List of engine specifications attributes. For details, see :ref:`Table 4 <modelarts_03_0073__en-us_topic_0131307648_table21589744151355>`. |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+

.. _modelarts_03_0073__en-us_topic_0131307648_table21589744151355:

.. table:: **Table 4** **engines** parameters

   +-----------------------+-----------------------+---------------------------------------------------+
   | Parameter             | Type                  | Description                                       |
   +=======================+=======================+===================================================+
   | engine_type           | Integer               | Engine type of a training job                     |
   |                       |                       |                                                   |
   |                       |                       | -  1: TensorFlow                                  |
   |                       |                       | -  5: Spark_MLlib                                 |
   |                       |                       | -  6: Scikit Learn                                |
   |                       |                       | -  9: XGBoost-Sklearn                             |
   |                       |                       | -  10: PyTorch                                    |
   |                       |                       | -  13: Ascend-Powered-Engine                      |
   |                       |                       | -  17: MindSpore-GPU                              |
   +-----------------------+-----------------------+---------------------------------------------------+
   | engine_id             | Long                  | ID of the engine selected for a training job      |
   +-----------------------+-----------------------+---------------------------------------------------+
   | engine_name           | String                | Name of the engine selected for a training job    |
   +-----------------------+-----------------------+---------------------------------------------------+
   | engine_version        | String                | Version of the engine selected for a training job |
   +-----------------------+-----------------------+---------------------------------------------------+

Samples
-------

The following shows how to query the engine specifications of a training job.

-  Sample request

   .. code-block::

      GET    https://endpoint/v1/{project_id}/job/ai-engines?job_type=train

-  Successful sample response

   .. code-block::

      {
          "is_success": true,
          "engines": [
              {
                  "engine_type": 1,
                  "engine_name": "TensorFlow",
                  "engine_id": 1,
                  "engine_version": "TF-1.4.0-python2.7"
              }
          ]
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
