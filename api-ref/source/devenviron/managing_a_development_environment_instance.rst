.. _modelarts_03_0115:

Managing a Development Environment Instance
===========================================

Function
--------

This API is used to startor stop a notebook instance.

URI
---

POST /v1/{project_id}/demanager/instances/{instance_id}/action

:ref:`Table 1 <modelarts_03_0115__en-us_topic_0136223954_table569625523811>` describes the required parameters.

.. _modelarts_03_0115__en-us_topic_0136223954_table569625523811:

.. table:: **Table 1** Parameters

   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                                 |
   +=============+===========+========+=============================================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Instance ID                                                                                                                 |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+

Request Body
------------

:ref:`Table 2 <modelarts_03_0115__en-us_topic_0136223954_table46411941555>` describes the request parameters.

.. _modelarts_03_0115__en-us_topic_0136223954_table46411941555:

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

:ref:`Table 3 <modelarts_03_0115__en-us_topic_0136223954_table14581542113111>` describes the response parameters.

.. _modelarts_03_0115__en-us_topic_0136223954_table14581542113111:

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

For details about the status code, see :ref:`Status Code <modelarts_03_0094>`.
