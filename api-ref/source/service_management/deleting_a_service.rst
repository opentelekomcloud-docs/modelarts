:original_name: DeleteService.html

.. _DeleteService:

Deleting a Service
==================

Function
--------

This API is used to delete a model service. You can delete your own services only.

URI
---

DELETE /v1/{project_id}/services/{service_id}

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                    |
   +============+===========+========+================================================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`.                       |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | service_id | Yes       | String | Service ID. To delete multiple services in a batch, use commas (,) to separate multiple **service_id** values. |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                           |
   +==============+===========+========+=======================================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. It can be obtained by calling the IAM API that is used to obtain a user token. The value of **X-Subject-Token** in the response header is the user token. |
   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Requests
----------------

The following shows how to delete the model service with ID **xxxxxx**.

.. code-block:: text

   DELETE https://endpoint/v1/{project_id}/services/xxxxxx

Example Responses
-----------------

**Status code: 200**

The service is deleted.

.. code-block::

   { }

Status Codes
------------

=========== =======================
Status Code Description
=========== =======================
200         The service is deleted.
=========== =======================

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
