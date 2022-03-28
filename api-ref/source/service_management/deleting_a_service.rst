Deleting a Service
==================

Function
--------

This API is used to delete a model service. You can delete your own services only.

URI
---

.. code-block::

   DELETE /v1/{project_id}/services/{service_id}

`Table 1 <#modelarts030089enustopic0130234312table10624434011>`__ describes the required parameters. 

.. _modelarts030089enustopic0130234312table10624434011:

.. table:: **Table 1** Parameters

   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                                                                      |
   +============+===========+========+==================================================================================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see `Obtaining a Project ID and Name <../common_parameters/obtaining_a_project_id_and_name.html#modelarts030147>`__. |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | service_id | Yes       | String | Service ID. If you want to delete multiple services in batches, use commas (,) to separate multiple **service_id** values.                                                       |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Body
------------

None

Response Body
-------------

None

Samples
-------

The following shows how to delete the model service whose ID is **xxxxxx**.

-  Sample request

   .. code-block::

      DELETE    https://endpoint/v1/{project_id}/services/xxxxxx

-  Sample response

   .. code-block::

      {}

Status Code
-----------

For details about the status code, see `Table 1 <../common_parameters/status_code.html#modelarts030094enustopic0132773864table1450010510213>`__.


