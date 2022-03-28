Modifying the Description of a Visualization Job
================================================

Function
--------

This API is used to modify the description of a visualization job.

URI
---

PUT /v1/{project_id}/visualization-jobs/{job_id}

`Table 1 <#modelarts030067enustopic0131202685table4247299117445>`__ describes the required parameters. 

.. _modelarts030067enustopic0131202685table4247299117445:

.. table:: **Table 1** Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                                                                         |
   +============+===========+========+=====================================================================================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see `Obtaining a Project ID and Name <../../common_parameters/obtaining_a_project_id_and_name.html#modelarts030147>`__. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | job_id     | Yes       | String | ID of a visualization job                                                                                                                                                           |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Body
------------

`Table 2 <#modelarts030067enustopic0131202685table212731411827>`__ describes the request parameters. 

.. _modelarts030067enustopic0131202685table212731411827:

.. table:: **Table 2** Parameters

   +-----------+-----------+--------+-----------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                       |
   +===========+===========+========+===================================================================================+
   | job_desc  | Yes       | String | Description of a visualization job. The value is a string of 0 to 256 characters. |
   +-----------+-----------+--------+-----------------------------------------------------------------------------------+

Response Body
-------------

`Table 3 <#modelarts030067enustopic0131202685table33036183111023>`__ describes the response parameters. 

.. _modelarts030067enustopic0131202685table33036183111023:

.. table:: **Table 3** Parameters

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                   |
   +=======================+=======================+===============================================================================================================+
   | is_success            | Boolean               | Whether the request is successful                                                                             |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------+
   | error_code            | String                | Error code of a failed API call. For details, see `Error Codes <../../common_parameters/error_codes.html>`__. |
   |                       |                       |                                                                                                               |
   |                       |                       | This parameter is not included when the API call succeeds.                                                    |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------+
   | error_message         | String                | Error message of a failed API call.                                                                           |
   |                       |                       |                                                                                                               |
   |                       |                       | This parameter is not included when the API call succeeds.                                                    |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------+

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

For details about the status code, see `Table 1 <../../common_parameters/status_code.html#modelarts030094enustopic0132773864table1450010510213>`__.


