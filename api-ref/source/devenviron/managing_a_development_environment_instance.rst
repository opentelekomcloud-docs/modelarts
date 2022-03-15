Managing a Development Environment Instance
===========================================

Function
--------

This API is used to startor stop a notebook instance.

URI
---

POST /v1/{project_id}/demanager/instances/{instance_id}/action

`Table 1 <#modelarts030115enustopic0136223954table569625523811>`__ describes the required parameters. 

.. _modelarts030115enustopic0136223954table569625523811:

.. table:: **Table 1** Parameters

   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                                                                                      |
   +=============+===========+========+==================================================================================================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain the project ID, see `Obtaining a Project ID and Name <../common_parameters/obtaining_a_project_id_and_name.html#modelarts030147>`__. |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Instance ID                                                                                                                                                                      |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Body
------------

`Table 2 <#modelarts030115enustopic0136223954table46411941555>`__ describes the request parameters. 

.. _modelarts030115enustopic0136223954table46411941555:

.. table:: **Table 2** Parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                  |
   +=================+=================+=================+==============================================================================+
   | action          | Yes             | String          | Operation on a development environment instance. The options are as follows: |
   |                 |                 |                 |                                                                              |
   |                 |                 |                 | -  **start**                                                                 |
   |                 |                 |                 | -  **stop**                                                                  |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------+

Response Body
-------------

`Table 3 <#modelarts030115enustopic0136223954table14581542113111>`__ describes the response parameters.



.. _modelarts030115enustopic0136223954table14581542113111:

.. table:: **Table 3** Parameters

   ============== ====== ==============================
   Parameter      Type   Description
   ============== ====== ==============================
   current_status String Current status of an instance
   previous_state String Previous status of an instance
   ============== ====== ==============================

Samples
-------

The following shows how to start instance **6fa459ea-ee8a-3ca4-894e-db77e160355e**.

-  Sample request

   .. code-block::

      {
          "action": "start"
      }

-  Successful sample response

   .. code-block::

      {
          "current_status": "STARTING",
          "previous_state": "STOPPED"
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


