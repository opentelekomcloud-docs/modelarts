.. _modelarts_03_0152:

Restarting an ML Studio Instance
================================

Function
--------

This API is used to restart an ML Studio development environment instance.

URI
---

POST /v1/{project_id}/demanager/instances/{instance_id}/action

:ref:`Table 1 <modelarts_03_0152__en-us_topic_0181453353_table569625523811>` describes the required parameters.

.. _modelarts_03_0152__en-us_topic_0181453353_table569625523811:

.. table:: **Table 1** Parameter description

   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                                 |
   +=============+===========+========+=============================================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Instance ID                                                                                                                 |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+

Request Body
------------

:ref:`Table 2 <modelarts_03_0152__en-us_topic_0181453353_table46411941555>` describes the request parameters.

.. _modelarts_03_0152__en-us_topic_0181453353_table46411941555:

.. table:: **Table 2** Parameter description

   +-----------+-----------+--------+--------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                    |
   +===========+===========+========+================================================================================+
   | action    | Yes       | String | Operation on a development environment instance. The value can be **restart**. |
   +-----------+-----------+--------+--------------------------------------------------------------------------------+

Response Body
-------------

:ref:`Table 3 <modelarts_03_0152__en-us_topic_0181453353_table1399617427385>` describes the response parameters.

.. _modelarts_03_0152__en-us_topic_0181453353_table1399617427385:

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

For details about the status code, see :ref:`Status Code <modelarts_03_0094>`.
