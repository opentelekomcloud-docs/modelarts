Deleting a Development Environment Instance
===========================================

Function
--------

This API is used to delete a development environment instance.

URI
---

DELETE /v1/{project_id}/demanager/instances/{instance_id}

`Table 1 <#modelarts030114enustopic0136223953table569625523811>`__ describes the required parameters. 

.. _modelarts030114enustopic0136223953table569625523811:

.. table:: **Table 1** Parameter description

   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                                                                                      |
   +=============+===========+========+==================================================================================================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain the project ID, see `Obtaining a Project ID and Name <../common_parameters/obtaining_a_project_id_and_name.html#modelarts030147>`__. |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Instance ID                                                                                                                                                                      |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Body
------------

None

Response Body
-------------

`Table 2 <#modelarts030114enustopic0136223953table14581542113111>`__ describes the response parameters.



.. _modelarts030114enustopic0136223953table14581542113111:

.. table:: **Table 2** Parameter description

   =========== ====== ===========
   Parameter   Type   Description
   =========== ====== ===========
   instance_id String Instance ID
   =========== ====== ===========

Samples
-------

The following shows how to delete instance **6fa459ea-ee8a-3ca4-894e-db77e160355e**.

-  Sample request

   .. code-block::

      DELETE https://endpoint/v1/{project_id}/demanager/instances/6fa459ea-ee8a-3ca4-894e-db77e160355e

-  Successful sample response

   .. code-block::

      {
          "instance_id": "6fa459ea-ee8a-3ca4-894e-db77e160355e"
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


