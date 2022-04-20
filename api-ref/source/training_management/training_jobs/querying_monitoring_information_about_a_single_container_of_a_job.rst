.. _modelarts_03_0150:

Querying Monitoring Information About a Single Container of a Job
=================================================================

Function
--------

This API is used to query monitoring information about a single container of a job.

URI
---

GET /v1/{project_id}/training-jobs/{job_id}/versions/{version_id}/pod/{pod_name}/metric-statistic

:ref:`Table 1 <modelarts_03_0150__en-us_topic_0188079018_table4442765616454>` describes the required parameters.

.. _modelarts_03_0150__en-us_topic_0188079018_table4442765616454:

.. table:: **Table 1** Parameter description

   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                                                                     |
   +============+===========+========+=================================================================================================================================================================================+
   | project_id | Yes       | String | Project ID                                                                                                                                                                      |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | job_id     | Yes       | Long   | ID of a training job                                                                                                                                                            |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version_id | Yes       | Long   | Version ID of a training job                                                                                                                                                    |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | pod_name   | Yes       | String | Container name, which is the same as the job log name. For details about how to obtain the value, see :ref:`Obtaining the Name of a Training Job Log File <modelarts_03_0054>`. |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Body
------------

:ref:`Table 2 <modelarts_03_0150__en-us_topic_0188079018_table87520312215>` describes the request parameters.

.. _modelarts_03_0150__en-us_topic_0188079018_table87520312215:

.. table:: **Table 2** Parameter description

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                            |
   +=================+=================+=================+========================================================================================================================================================+
   | metrics         | No              | String          | Metrics to be queried. Separate metrics by commas (,), for example, **CpuUsage,MemUsage**. If this parameter is left blank, all metrics are queried.   |
   |                 |                 |                 |                                                                                                                                                        |
   |                 |                 |                 | Options:                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                        |
   |                 |                 |                 | -  CpuUsage                                                                                                                                            |
   |                 |                 |                 | -  MemUsage                                                                                                                                            |
   |                 |                 |                 | -  DiskReadRate                                                                                                                                        |
   |                 |                 |                 | -  DiskWriteRate                                                                                                                                       |
   |                 |                 |                 | -  RecvBytesRate                                                                                                                                       |
   |                 |                 |                 | -  SendBytesRate                                                                                                                                       |
   |                 |                 |                 | -  GpuUtil                                                                                                                                             |
   |                 |                 |                 | -  GpuMemUsage                                                                                                                                         |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | statistic_type  | No              | String          | Metric statistics method, indicating whether to collect metric statistics based on a single GPU. This parameter applies only to GPU metric statistics. |
   |                 |                 |                 |                                                                                                                                                        |
   |                 |                 |                 | -  **all**: Obtain the average value of the metric.                                                                                                    |
   |                 |                 |                 | -  **each**: Obtain the metric monitoring information about each GPU.                                                                                  |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Body
-------------

:ref:`Table 3 <modelarts_03_0150__en-us_topic_0188079018_table1414514116749>` describes the response parameters.

.. _modelarts_03_0150__en-us_topic_0188079018_table1414514116749:

.. table:: **Table 3** Parameter description

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                |
   +=======================+=======================+============================================================================================================================+
   | error_message         | String                | Error message when the API call fails.                                                                                     |
   |                       |                       |                                                                                                                            |
   |                       |                       | This parameter is not included when the API call succeeds.                                                                 |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------+
   | error_code            | String                | Error code when the API call fails. For details, see :ref:`Error Codes <modelarts_03_0095>`.                               |
   |                       |                       |                                                                                                                            |
   |                       |                       | This parameter is not included when the API call succeeds.                                                                 |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------+
   | metrics               | JSON Array            | Metric monitoring details. For details, see :ref:`Table 4 <modelarts_03_0150__en-us_topic_0188079018_table8361164171810>`. |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------+
   | interval              | Integer               | Query interval, in minutes.                                                                                                |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------+

.. _modelarts_03_0150__en-us_topic_0188079018_table8361164171810:

.. table:: **Table 4** **metrics** data structure

   +-----------+------------+---------------------------------------------------------------------------+
   | Parameter | Type       | Description                                                               |
   +===========+============+===========================================================================+
   | metric    | String     | Monitoring metrics                                                        |
   +-----------+------------+---------------------------------------------------------------------------+
   | value     | JSON Array | Sequence of the obtained metric value. The element is of the String type. |
   +-----------+------------+---------------------------------------------------------------------------+

Samples
-------

The following shows how to query the logs contained in **log1.log** of the job whose **job_id** is **10** and **version_id** is **10**.

-  Sample request

   .. code-block::

      GET    https://endpoint/v1/{project_id}/training-jobs/10/versions/10/pod/pod1/metric-statistic?metrics=gpuUtil

-  Successful sample response

   .. code-block::

      {
        "metrics":
        [
          {
             "metric":"gpuUtil",
             "value":["1","22","33"]
           }
        ],
        "interval" : 1
      }

-  Failed sample response

   .. code-block::

      {
          "error_message": "Error string",
          "error_code": "ModelArts.0105"
      }

Status Code
-----------

For details about the status code, see :ref:`Status Code <modelarts_03_0094>`.
