:original_name: modelarts_03_0114.html

.. _modelarts_03_0114:

Deleting a Development Environment Instance
===========================================

Function
--------

This API is used to delete a development environment instance.

URI
---

DELETE /v1/{project_id}/demanager/instances/{instance_id}

:ref:`Table 1 <en-us_topic_0000001909747424__table569625523811>` describes the required parameters.

.. _en-us_topic_0000001909747424__table569625523811:

.. table:: **Table 1** Parameter description

   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                               |
   +=============+===========+========+===========================================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Instance ID                                                                                                               |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+

Request Body
------------

None

Response Body
-------------

:ref:`Table 2 <en-us_topic_0000001909747424__table14581542113111>` describes the response parameters.

.. _en-us_topic_0000001909747424__table14581542113111:

.. table:: **Table 2** Parameter description

   =========== ====== ===========
   Parameter   Type   Description
   =========== ====== ===========
   instance_id String Instance ID
   =========== ====== ===========

Sample Request
--------------

The following shows how to delete instance **6fa459ea-ee8a-3ca4-894e-db77e160355e**.

.. code-block:: text

   DELETE https://endpoint/v1/{project_id}/demanager/instances/6fa459ea-ee8a-3ca4-894e-db77e160355e

Sample Response
---------------

-  Successful response

   .. code-block::

      {
          "instance_id": "6fa459ea-ee8a-3ca4-894e-db77e160355e"
      }

-  Failed response

   .. code-block::

      {
          "error_message": "The instance does not exist.",
          "error_code": "ModelArts.6309"
      }

Status Code
-----------

For details about the status code, see :ref:`Status Code <modelarts_03_0094>`.
