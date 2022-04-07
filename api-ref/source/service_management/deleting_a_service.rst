.. _modelarts_03_0089:

Deleting a Service
==================

Function
--------

This API is used to delete a model service. You can delete your own services only.

URI
---

.. code-block::

   DELETE /v1/{project_id}/services/{service_id}

:ref:`Table 1 <modelarts_03_0089__en-us_topic_0130234312_table10624434011>` describes the required parameters.

.. _modelarts_03_0089__en-us_topic_0130234312_table10624434011:

.. table:: **Table 1** Parameters

   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                 |
   +============+===========+========+=============================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | service_id | Yes       | String | Service ID. If you want to delete multiple services in batches, use commas (,) to separate multiple **service_id** values.  |
   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+

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

For details about the status code, see :ref:`Table 1 <modelarts_03_0094__en-us_topic_0132773864_table1450010510213>`.
