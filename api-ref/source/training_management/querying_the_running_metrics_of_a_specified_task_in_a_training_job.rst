:original_name: ShowTrainingJobMetrics.html

.. _ShowTrainingJobMetrics:

Querying the Running Metrics of a Specified Task in a Training Job
==================================================================

Function
--------

This API is used to query the running metrics of a specified task in a training job.

URI
---

GET /v2/{project_id}/training-jobs/{training_job_id}/metrics/{task_id}

.. table:: **Table 1** Path Parameters

   +-----------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory | Type   | Description                                                                                                              |
   +=================+===========+========+==========================================================================================================================+
   | project_id      | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`.                                 |
   +-----------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | training_job_id | Yes       | String | Training job ID For details about how to obtain the value, see :ref:`Querying the Training Job List <listtrainingjobs>`. |
   +-----------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | task_id         | Yes       | String | Name of a training job. You can obtain the value from the **status.tasks** field in the training job details.            |
   +-----------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | project_id      | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`.                                 |
   +-----------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | training_job_id | Yes       | String | Training job ID For details about how to obtain the value, see :ref:`Querying the Training Job List <listtrainingjobs>`. |
   +-----------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+
   | task_id         | Yes       | String | Name of a training job. You can obtain the value from the **status.tasks** field in the training job details.            |
   +-----------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   +-----------+-------------------------------------------------------------------------------------------------------------------------+------------------+
   | Parameter | Type                                                                                                                    | Description      |
   +===========+=========================================================================================================================+==================+
   | metrics   | Array of :ref:`MetricObject <en-us_topic_0000002268806213__en-us_topic_0000002055322438_response_metricobject>` objects | Running metrics. |
   +-----------+-------------------------------------------------------------------------------------------------------------------------+------------------+

.. _en-us_topic_0000002268806213__en-us_topic_0000002055322438_response_metricobject:

.. table:: **Table 3** MetricObject

   +-----------------------+-----------------------+------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                            |
   +=======================+=======================+========================================================================+
   | metric                | String                | Running metric. The options are as follows:                            |
   |                       |                       |                                                                        |
   |                       |                       | -  **cpuUsage**: CPU usage                                             |
   |                       |                       |                                                                        |
   |                       |                       | -  **memUsage**: physical memory usage                                 |
   |                       |                       |                                                                        |
   |                       |                       | -  **gpuUtil**: GPU usage                                              |
   |                       |                       |                                                                        |
   |                       |                       | -  **gpuMemUsage**: GPU memory usage                                   |
   |                       |                       |                                                                        |
   |                       |                       | -  **npuUtil**: NPU usage                                              |
   |                       |                       |                                                                        |
   |                       |                       | -  **npuMemUsage**: NPU memory usage                                   |
   +-----------------------+-----------------------+------------------------------------------------------------------------+
   | value                 | Array of doubles      | Value of a running metric. An average value is collected every minute. |
   +-----------------------+-----------------------+------------------------------------------------------------------------+

Example Requests
----------------

The following shows how to query the running metrics of the **work-0** task of the training job whose UUID is **2cd88daa-31a4-40a8-a58f-d186b0e93e4f**.

.. code-block:: text

   GET https://endpoint/v2/{project_id}/training-jobs/2cd88daa-31a4-40a8-a58f-d186b0e93e4f/metrics/worker-0

Example Responses
-----------------

**Status code: 200**

ok

.. code-block::

   {
     "metrics" : [ {
       "metric" : "cpuUsage",
       "value" : [ -1, -1, 2.43, 4.524, 6.714, 12.422, 9.214, 5.36, 7.5, 10.088, 8.975, 11.423, 11.548, 14.563, 16.833 ]
     }, {
       "metric" : "memUsage",
       "value" : [ -1, -1, 0.04, 0.521, 1.652, 4.252, 6.433, 7.384, 7.982, 8.718, 9.365, 9.881, 10.192, 9.994, 9.005 ]
     }, {
       "metric" : "gpuUtil",
       "value" : [ -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1 ]
     }, {
       "metric" : "gpuMemUsage",
       "value" : [ -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1 ]
     }, {
       "metric" : "npuUtil",
       "value" : [ -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1 ]
     }, {
       "metric" : "npuMemUsage",
       "value" : [ -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1 ]
     } ]
   }

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
200         ok
=========== ===========

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
