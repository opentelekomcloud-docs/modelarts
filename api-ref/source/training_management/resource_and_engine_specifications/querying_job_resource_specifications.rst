.. _modelarts_03_0072:

Querying Job Resource Specifications
====================================

Function
--------

This API is used to query the resource specifications of a specified job.

You must specify the resource specifications when creating a training job or an inference job.

URI
---

GET /v1/{project_id}/job/resource-specs

:ref:`Table 1 <modelarts_03_0072__en-us_topic_0131307647_table5822680595335>` describes the required parameters.

.. _modelarts_03_0072__en-us_topic_0131307647_table5822680595335:

.. table:: **Table 1** Parameters

   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                 |
   +============+===========+========+=============================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Parameters

   +--------------+-----------+---------+--------------------------------------------------------+
   | Parameter    | Mandatory | Type    | Description                                            |
   +==============+===========+=========+========================================================+
   | job_type     | No        | String  | Job type. The value can be **train** or **inference**. |
   +--------------+-----------+---------+--------------------------------------------------------+
   | engine_id    | No        | Long    | Engine ID of a job. Default value: **0**               |
   +--------------+-----------+---------+--------------------------------------------------------+
   | project_type | No        | Integer | Project type. Default value: **0**                     |
   +--------------+-----------+---------+--------------------------------------------------------+

Request Body
------------

None

Response Body
-------------

:ref:`Table 3 <modelarts_03_0072__en-us_topic_0131307647_table1817887315129>` describes the response parameters.

.. _modelarts_03_0072__en-us_topic_0131307647_table1817887315129:

.. table:: **Table 3** Parameters

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                  |
   +=======================+=======================+==============================================================================================================================================+
   | is_success            | Boolean               | Whether the request is successful                                                                                                            |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | error_message         | String                | Error message of a failed API call.                                                                                                          |
   |                       |                       |                                                                                                                                              |
   |                       |                       | This parameter is not included when the API call succeeds.                                                                                   |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | error_code            | String                | Error code of a failed API call. For details, see :ref:`Error Codes <modelarts_03_0095>`.                                                    |
   |                       |                       |                                                                                                                                              |
   |                       |                       | This parameter is not included when the API call succeeds.                                                                                   |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | spec_total_count      | Integer               | Total number of job resource specifications                                                                                                  |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
   | specs                 | **specs** array       | List of resource specifications attributes. For details, see :ref:`Table 4 <modelarts_03_0072__en-us_topic_0131307647_table20408880151239>`. |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+

.. _modelarts_03_0072__en-us_topic_0131307647_table20408880151239:

.. table:: **Table 4** **specs** parameters

   +----------------+---------+--------------------------------------------------------------------------------------------------------------------+
   | Parameter      | Type    | Description                                                                                                        |
   +================+=========+====================================================================================================================+
   | spec_id        | Long    | ID of the resource specifications                                                                                  |
   +----------------+---------+--------------------------------------------------------------------------------------------------------------------+
   | core           | String  | Number of cores of the resource specifications                                                                     |
   +----------------+---------+--------------------------------------------------------------------------------------------------------------------+
   | cpu            | String  | CPU memory of the resource specifications                                                                          |
   +----------------+---------+--------------------------------------------------------------------------------------------------------------------+
   | gpu_num        | Integer | Number of GPUs of the resource specifications                                                                      |
   +----------------+---------+--------------------------------------------------------------------------------------------------------------------+
   | gpu_type       | String  | GPU type of the resource specifications                                                                            |
   +----------------+---------+--------------------------------------------------------------------------------------------------------------------+
   | spec_code      | String  | Type of the resource specifications                                                                                |
   +----------------+---------+--------------------------------------------------------------------------------------------------------------------+
   | max_num        | Integer | Maximum number of nodes that can be selected                                                                       |
   +----------------+---------+--------------------------------------------------------------------------------------------------------------------+
   | unit_num       | Integer | Number of pricing units                                                                                            |
   +----------------+---------+--------------------------------------------------------------------------------------------------------------------+
   | storage        | String  | SSD size of a resource flavor                                                                                      |
   +----------------+---------+--------------------------------------------------------------------------------------------------------------------+
   | interface_type | Integer | Interface type                                                                                                     |
   +----------------+---------+--------------------------------------------------------------------------------------------------------------------+
   | no_resource    | Boolean | Whether the resources of the selected specifications are sufficient. True indicates that no resource is available. |
   +----------------+---------+--------------------------------------------------------------------------------------------------------------------+

Samples
-------

The following shows how to query the resource specifications of a training job.

-  Sample request

   .. code-block::

      GET    https://endpoint/v1/{project_id}/job/resource-specs?job_type=train

-  Successful sample response

   .. code-block::

      {
          "specs": [

              {
                  "spec_id": 2,
                  "core": "2",
                  "cpu": "8",
                  "gpu_num": 0,
                  "gpu_type": "",
                  "spec_code": "modelarts.vm.cpu.2u",
                  "unit_num": 1,
                  "max_num": 2,
                  "storage": "",
                  "interface_type": 1,
                  "no_resource": false
              },
              {
                  "spec_id": 4,
                  "core": "8",
                  "cpu": "64",
                  "gpu_num": 1,
                  "gpu_type": "v100",
                  "spec_code":"modelarts.vm.gpu.v100",
                  "unit_num": 1,
                  "max_num": 4,
                  "storage": "",
                  "interface_type": 1,
                  "no_resource": false
              }
          ],
          "is_success": true,
          "spec_total_count": 2
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
