:original_name: modelarts_03_0115.html

.. _modelarts_03_0115:

Managing a Development Environment Instance
===========================================

Function
--------

This API is used to startor stop a notebook instance.

URI
---

POST /v1/{project_id}/demanager/instances/{instance_id}/action

:ref:`Table 1 <en-us_topic_0000001943866569__table569625523811>` describes the required parameters.

.. _en-us_topic_0000001943866569__table569625523811:

.. table:: **Table 1** Parameters

   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                               |
   +=============+===========+========+===========================================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Instance ID                                                                                                               |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+

Request Body
------------

:ref:`Table 2 <en-us_topic_0000001943866569__table46411941555>` describes the request parameters.

.. _en-us_topic_0000001943866569__table46411941555:

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

:ref:`Table 3 <en-us_topic_0000001943866569__table14581542113111>` describes the response parameters.

.. _en-us_topic_0000001943866569__table14581542113111:

.. table:: **Table 3** Parameters

   ============== ====== ==============================
   Parameter      Type   Description
   ============== ====== ==============================
   current_status String Current status of an instance
   previous_state String Previous status of an instance
   ============== ====== ==============================

Sample Request
--------------

The following shows how to start instance **6fa459ea-ee8a-3ca4-894e-db77e160355e**.

.. code-block::

   {
       "action": "start"
   }

Sample Response
---------------

-  Successful response

   .. code-block::

      {
          "current_status": "STARTING",
          "previous_state": "STOPPED"
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
