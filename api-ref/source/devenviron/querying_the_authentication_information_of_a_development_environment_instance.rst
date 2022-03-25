Querying the Authentication Information of a Development Environment Instance
=============================================================================

Function
--------

This API is used to query the authentication information of a development environment instance, which is used to open the development environment instance.

URI
---

GET /v1/{project_id}/demanager/instances/{instance_id}/token

`Table 1 <#modelarts030109enustopic0136223948table569625523811>`__ describes the required parameters. 

.. _modelarts030109enustopic0136223948table569625523811:

.. table:: **Table 1** Parameter description

   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
   +=============+===========+========+=========================================================================================================================================================================================================================================================================================================================================================================================================================================================================================+
   | project_id  | Yes       | String | Project ID                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Instance ID It is the ID of the development environment instance you create. The instance ID is contained in the response code after the instance has been created. For details, see `Creating a Development Environment Instance <../devenviron/creating_a_development_environment_instance.html#modelarts030110>`__. If the development environment instance is created on the ModelArts management console, you can view the ID of the instance on the ModelArts management console. |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Body
------------

None

Response Body
-------------

`Table 2 <#modelarts030109enustopic0136223948table973120224596>`__ describes the response parameters. 

.. _modelarts030109enustopic0136223948table973120224596:

.. table:: **Table 2** Parameter description

   ========= ====== ====================
   Parameter Type   Description
   ========= ====== ====================
   token     String Authentication token
   ========= ====== ====================

Samples
-------

The following shows how to obtain the authentication token of instance **6fa459ea-ee8a-3ca4-894e-db77e160355e**.

-  Sample request

   .. code-block::

      GET https://endpoint/v1/{project_id}/demanager/instances/6fa459ea-ee8a-3ca4-894e-db77e160355e/token

-  Successful sample response

   .. code-block::

      {
          "token": "7211546f57cd432790643bb6612da19d"
      }

-  Failed sample response

   .. code-block::

      {
          "error_message": "The instance does not exist.",
          "error_code": "ModelArts.6309"
      }

Status Code
-----------

For details about the status code, see `Status Code <../common_parameters/status_code.html#modelarts030094>`__.


