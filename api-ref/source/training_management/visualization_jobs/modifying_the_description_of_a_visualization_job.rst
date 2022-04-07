.. _modelarts_03_0067:

Modifying the Description of a Visualization Job
================================================

Function
--------

This API is used to modify the description of a visualization job.

URI
---

PUT /v1/{project_id}/visualization-jobs/{job_id}

:ref:`Table 1 <modelarts_03_0067__en-us_topic_0131202685_table4247299117445>` describes the required parameters.

.. _modelarts_03_0067__en-us_topic_0131202685_table4247299117445:

.. table:: **Table 1** Parameters

   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                 |
   +============+===========+========+=============================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | job_id     | Yes       | String | ID of a visualization job                                                                                                   |
   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+

Request Body
------------

:ref:`Table 2 <modelarts_03_0067__en-us_topic_0131202685_table212731411827>` describes the request parameters.

.. _modelarts_03_0067__en-us_topic_0131202685_table212731411827:

.. table:: **Table 2** Parameters

   +-----------+-----------+--------+-----------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                       |
   +===========+===========+========+===================================================================================+
   | job_desc  | Yes       | String | Description of a visualization job. The value is a string of 0 to 256 characters. |
   +-----------+-----------+--------+-----------------------------------------------------------------------------------+

Response Body
-------------

:ref:`Table 3 <modelarts_03_0067__en-us_topic_0131202685_table33036183111023>` describes the response parameters.

.. _modelarts_03_0067__en-us_topic_0131202685_table33036183111023:

.. table:: **Table 3** Parameters

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                               |
   +=======================+=======================+===========================================================================================+
   | is_success            | Boolean               | Whether the request is successful                                                         |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------+
   | error_code            | String                | Error code of a failed API call. For details, see :ref:`Error Codes <modelarts_03_0095>`. |
   |                       |                       |                                                                                           |
   |                       |                       | This parameter is not included when the API call succeeds.                                |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------+
   | error_message         | String                | Error message of a failed API call.                                                       |
   |                       |                       |                                                                                           |
   |                       |                       | This parameter is not included when the API call succeeds.                                |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------+

Samples
-------

The following shows how to modify the description of the visualization job whose ID is **10** to **This is a ModelArts job**.

-  Sample request

   .. code-block::

      PUT https://endpoint/v1/{project_id}/visualization-jobs/10
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
          "error_message": "Illegal name: %%123",
          "error_code": "ModelArts.0104"
      }

Status Code
-----------

For details about the status code, see :ref:`Table 1 <modelarts_03_0094__en-us_topic_0132773864_table1450010510213>`.
