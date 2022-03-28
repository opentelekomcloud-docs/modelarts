Restarting an ML Studio Instance
================================

Function
--------

This API is used to restart an ML Studio development environment instance.

URI
---

POST /v1/{project_id}/demanager/instances/{instance_id}/action

`Table 1 <#modelarts030152enustopic0181453353table569625523811>`__ describes the required parameters.



.. _modelarts030152enustopic0181453353table569625523811:

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

`Table 2 <#modelarts030152enustopic0181453353table46411941555>`__ describes the request parameters.



.. _modelarts030152enustopic0181453353table46411941555:

.. table:: **Table 2** Parameter description

   +-----------+-----------+--------+--------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                    |
   +===========+===========+========+================================================================================+
   | action    | Yes       | String | Operation on a development environment instance. The value can be **restart**. |
   +-----------+-----------+--------+--------------------------------------------------------------------------------+

Response Body
-------------

`Table 3 <#modelarts030152enustopic0181453353table1399617427385>`__ describes the response parameters.



.. _modelarts030152enustopic0181453353table1399617427385:

.. table:: **Table 3** Parameter description

   ============== ====== ==============================
   Parameter      Type   Description
   ============== ====== ==============================
   current_status String Current status of an instance
   previous_state String Previous status of an instance
   ============== ====== ==============================

Samples
-------

The following shows how to restart the ML Studio instance whose ID is **47cf4ff3-0c59-44fe-9821-2840a34c02a9**.

-  Sample request

   .. code-block::

      {
          "action": "restart"
      }

-  Sample response

   .. code-block::

      {
      "current_status": "REBOOTING",
      "previous_state": "ACTIVE"
      }

Status Code
-----------

For details about the status code, see `Status Code <../common_parameters/status_code.html#modelarts030094>`__.


