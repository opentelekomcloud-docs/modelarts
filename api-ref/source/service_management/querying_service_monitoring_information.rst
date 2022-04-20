.. _modelarts_03_0087:

Querying Service Monitoring Information
=======================================

Function
--------

This API is used to query service monitoring information.

URI
---

GET /v1/{project_id}/services/{service_id}/monitor

:ref:`Table 1 <modelarts_03_0087__en-us_topic_0130048742_table10624434011>` describes the required parameters.

.. _modelarts_03_0087__en-us_topic_0130048742_table10624434011:

.. table:: **Table 1** Parameters

   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                 |
   +============+===========+========+=============================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | service_id | Yes       | String | Service ID                                                                                                                  |
   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Parameters

   +-----------+-----------+--------+------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                      |
   +===========+===========+========+==================================================================+
   | node_id   | No        | String | ID of the node to be queried. By default, all nodes are queried. |
   +-----------+-----------+--------+------------------------------------------------------------------+

Request Body
------------

None

Response Body
-------------

:ref:`Table 3 <modelarts_03_0087__en-us_topic_0130048742_table413209485>` describes the response parameters.

.. _modelarts_03_0087__en-us_topic_0130048742_table413209485:

.. table:: **Table 3** Parameters

   +--------------+----------------------------------------------------------------+--------------------+
   | Parameter    | Type                                                           | Description        |
   +==============+================================================================+====================+
   | service_id   | String                                                         | Service ID         |
   +--------------+----------------------------------------------------------------+--------------------+
   | service_name | String                                                         | Service name       |
   +--------------+----------------------------------------------------------------+--------------------+
   | monitors     | **monitor** array corresponding to **infer_type** of a service | Monitoring details |
   +--------------+----------------------------------------------------------------+--------------------+

.. table:: **Table 4** **monitor** parameters of **real-time**

   ================ ======= =====================================
   Parameter        Type    Description
   ================ ======= =====================================
   model_id         String  Model ID
   model_name       String  Model name
   model_version    String  Model version
   invocation_times Long    Total number of model instance calls
   failed_times     Long    Number of failed model instance calls
   cpu_core_usage   Float   Number of used CPUs
   cpu_core_total   Float   Total number of CPUs
   cpu_memory_usage Integer Used memory, in MB
   cpu_memory_total Integer Total memory, in MB
   gpu_usage        Float   Number used GPUs
   gpu_total        Float   Total number of GPUs
   ================ ======= =====================================

Samples
-------

The following shows how to query the monitoring information about a real-time service.

-  Sample request

   .. code-block::

      GET    https://endpoint/v1/{project_id}/services/{service_id}/monitor

-  Sample response

   .. code-block::

      {
          "service_id": "xxx",
          "service_name": "mnist",
          "monitors": 
          [{
              "model_id": "xxxx",
              "model_name": "minst",
              "model_version": "1.0.0",
              "invocation_times": 50,
              "failed_times": 1,
              "cpu_core_usage": "2.4",
              "cpu_core_total": "4",
              "cpu_memory_usage": "2011",
              "cpu_memory_total": "8192",
              "gpu_usage": "0.6",
              "gpu_total": "1"
         } ]
      }

Status Code
-----------

For details about the status code, see :ref:`Table 1 <modelarts_03_0094__en-us_topic_0132773864_table1450010510213>`.
