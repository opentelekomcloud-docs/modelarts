:original_name: ShowPoolMonitor.html

.. _ShowPoolMonitor:

Monitoring a Resource Pool
==========================

Function
--------

This API is used to obtain the monitored resource pool information.

URI
---

GET /v2/{project_id}/pools/{pool_name}/monitor

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                              |
   +============+===========+========+==========================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | pool_name  | Yes       | String | Resource pool ID. The value is the **metadata.name** field in the resource pool details. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                                                                                                                         |
   +=================+=================+=================+=====================================================================================================================================================================================================================================================================================================================================================================================================+
   | time_range      | No              | String          | Time range for query. The default value is **-1.-1.60**. The format is startTimeInMillis.endTimeInMillis.durationInMinutes. Parameter description:                                                                                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                 | -  **startTimeInMillis**: Start time (UTC) of the query, in milliseconds. If this parameter is set to **-1**, the server calculates the start time as follows: endTimeInMillis - durationInMinutes x 60 x 1000.                                                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                 | -  **endTimeInMillis**: End time (UTC) of the query, in milliseconds. If this parameter is set to **-1**, the server calculates the end time as follows: startTimeInMillis + durationInMinutes x 60 x 1000. If the calculated end time is later than the current system time, the current system time is used.                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                 | -  **durationInMinutes**: Time span, in minutes. The value must be greater than **0**, and also greater than or equal to the result of "(endTimeInMillis - startTimeInMillis)/(60 x 1000) - 1".                                                                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                 |    If both the start time and end time are set to **-1**, the system sets the end time to the current UTC time (in milliseconds) and calculates the start time as follows: endTimeInMillis - durationInMinutes x 60 x 1000. For example, **-1.-1.60** indicates the latest 60 minutes. Constraint: In a single request, the following condition must be met: durationInMinutes x 60/period <= 1440. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | statistics      | No              | String          | Statistical mode. The options are as follows:                                                                                                                                                                                                                                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                 | -  **maximum**: maximum value statistics (default setting)                                                                                                                                                                                                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                 | -  **minimum**: minimum value statistics                                                                                                                                                                                                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                 | -  **sum**: sum statistics                                                                                                                                                                                                                                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                 | -  **average**: average value statistics                                                                                                                                                                                                                                                                                                                                                            |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | period          | No              | String          | Monitoring data granularity, in seconds. The options are as follows:                                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                 | -  **60**: The granularity is 1 minute, which is the default value.                                                                                                                                                                                                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                 | -  **300**: The granularity is 5 minutes.                                                                                                                                                                                                                                                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                 | -  **900**: The granularity is 15 minutes.                                                                                                                                                                                                                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                 | -  **3600**: The granularity is 1 hour.                                                                                                                                                                                                                                                                                                                                                             |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------+------------------------------------------------------------------------------------------------+------------------------------------------------------------------+
   | Parameter | Type                                                                                           | Description                                                      |
   +===========+================================================================================================+==================================================================+
   | metrics   | Array of :ref:`PoolMetricItem <en-us_topic_0000002341058270__response_poolmetricitem>` objects | Metric list. The JSON array can contain a maximum of 20 metrics. |
   +-----------+------------------------------------------------------------------------------------------------+------------------------------------------------------------------+

.. _en-us_topic_0000002341058270__response_poolmetricitem:

.. table:: **Table 4** PoolMetricItem

   +------------+----------------------------------------------------------------------------------------------------------+--------------+
   | Parameter  | Type                                                                                                     | Description  |
   +============+==========================================================================================================+==============+
   | metric     | Array of :ref:`PoolMetricItemValue <en-us_topic_0000002341058270__response_poolmetricitemvalue>` objects | Metrics.     |
   +------------+----------------------------------------------------------------------------------------------------------+--------------+
   | dataPoints | Array of :ref:`PoolMetricDataPoint <en-us_topic_0000002341058270__response_poolmetricdatapoint>` objects | Key metrics. |
   +------------+----------------------------------------------------------------------------------------------------------+--------------+

.. _en-us_topic_0000002341058270__response_poolmetricitemvalue:

.. table:: **Table 5** PoolMetricItemValue

   +-----------------------+------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                                             | Description                                                                             |
   +=======================+==================================================================================================================+=========================================================================================+
   | metricName            | String                                                                                                           | Metric name. The options are as follows:                                                |
   |                       |                                                                                                                  |                                                                                         |
   |                       |                                                                                                                  | -  **cpuUsage**: CPU usage                                                              |
   |                       |                                                                                                                  |                                                                                         |
   |                       |                                                                                                                  | -  **memUsedRate**: memory usage                                                        |
   |                       |                                                                                                                  |                                                                                         |
   |                       |                                                                                                                  | -  **gpuUtil**: GPU usage                                                               |
   |                       |                                                                                                                  |                                                                                         |
   |                       |                                                                                                                  | -  **gpuMemUsage**: used GPU memory                                                     |
   |                       |                                                                                                                  |                                                                                         |
   |                       |                                                                                                                  | -  **npuUtil**: NPU usage                                                               |
   |                       |                                                                                                                  |                                                                                         |
   |                       |                                                                                                                  | -  **npuMemUsage**: used NPU memory                                                     |
   |                       |                                                                                                                  |                                                                                         |
   |                       |                                                                                                                  | -  **diskCapacity**: disk capacity                                                      |
   |                       |                                                                                                                  |                                                                                         |
   |                       |                                                                                                                  | -  **diskAvailableCapacity**: available disk capacity                                   |
   |                       |                                                                                                                  |                                                                                         |
   |                       |                                                                                                                  | -  **diskUsedRate**: disk usage                                                         |
   +-----------------------+------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+
   | namespace             | String                                                                                                           | Metric namespace. The options are as follows:                                           |
   |                       |                                                                                                                  |                                                                                         |
   |                       |                                                                                                                  | -  **PAAS.CONTAINER**: namespace of component, instance, process, and container metrics |
   |                       |                                                                                                                  |                                                                                         |
   |                       |                                                                                                                  | -  **PAAS.NODE**: namespace of host, network, disk, and file system metrics             |
   |                       |                                                                                                                  |                                                                                         |
   |                       |                                                                                                                  | -  **PAAS.SLA**: namespace of SLA metrics                                               |
   |                       |                                                                                                                  |                                                                                         |
   |                       |                                                                                                                  | -  **PAAS.AGGR**: namespace of cluster metrics                                          |
   |                       |                                                                                                                  |                                                                                         |
   |                       |                                                                                                                  | -  **CUSTOMMETRICS**: default namespace of custom metrics                               |
   +-----------------------+------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+
   | dimensions            | Array of :ref:`PoolMetricDimensionItem <en-us_topic_0000002341058270__response_poolmetricdimensionitem>` objects | Dimensions.                                                                             |
   +-----------------------+------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+

.. _en-us_topic_0000002341058270__response_poolmetricdimensionitem:

.. table:: **Table 6** PoolMetricDimensionItem

   ========= ====== =======================
   Parameter Type   Description
   ========= ====== =======================
   name      String Metric dimension name.
   value     String Metric dimension value.
   ========= ====== =======================

.. _en-us_topic_0000002341058270__response_poolmetricdatapoint:

.. table:: **Table 7** PoolMetricDataPoint

   +------------+--------------------------------------------------------------------------------------------------------------------+-----------------------------+
   | Parameter  | Type                                                                                                               | Description                 |
   +============+====================================================================================================================+=============================+
   | timestamp  | Integer                                                                                                            | Timestamp.                  |
   +------------+--------------------------------------------------------------------------------------------------------------------+-----------------------------+
   | unit       | String                                                                                                             | Time series unit.           |
   +------------+--------------------------------------------------------------------------------------------------------------------+-----------------------------+
   | statistics | Array of :ref:`PoolMetricDataPointValue <en-us_topic_0000002341058270__response_poolmetricdatapointvalue>` objects | List of statistical values. |
   +------------+--------------------------------------------------------------------------------------------------------------------+-----------------------------+

.. _en-us_topic_0000002341058270__response_poolmetricdatapointvalue:

.. table:: **Table 8** PoolMetricDataPointValue

   +-----------------------+-----------------------+--------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                  |
   +=======================+=======================+==============================================================+
   | statistic             | String                | Statistical mode. The options are as follows:                |
   |                       |                       |                                                              |
   |                       |                       | -  **maximum**: maximum value statistics                     |
   |                       |                       |                                                              |
   |                       |                       | -  **average**: average value statistics                     |
   +-----------------------+-----------------------+--------------------------------------------------------------+
   | value                 | Float                 | Statistical result. The value **-1** indicates invalid data. |
   +-----------------------+-----------------------+--------------------------------------------------------------+

**Status code: 404**

.. table:: **Table 9** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Obtain the monitored resource pool information.

.. code-block:: text

   GET https://{endpoint}/v2/{project_id}/pools/{pool_name}/monitor

   { }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "metrics" : [ {
       "metric" : {
         "dimensions" : [ {
           "name" : "clusterId",
           "value" : "83df17f1-d74c-11ec-a070-0255ac1000c3"
         } ],
         "metricName" : "cpuUsage",
         "namespace" : "PAAS.AGGR"
       },
       "dataPoints" : [ {
         "timestamp" : 1655193600000,
         "unit" : "Percent",
         "statistics" : [ {
           "statistic" : "average",
           "value" : 7.944
         } ]
       }, {
         "timestamp" : 1655197200000,
         "unit" : "Percent",
         "statistics" : [ {
           "statistic" : "average",
           "value" : 7.88
         } ]
       } ]
     }, {
       "metric" : {
         "dimensions" : [ {
           "name" : "clusterId",
           "value" : "83df17f1-d74c-11ec-a070-0255ac1000c3"
         } ],
         "metricName" : "memUsedRate",
         "namespace" : "PAAS.AGGR"
       },
       "dataPoints" : [ {
         "timestamp" : 1655193600000,
         "unit" : "Percent",
         "statistics" : [ {
           "statistic" : "average",
           "value" : 13.83
         } ]
       }, {
         "timestamp" : 1655197200000,
         "unit" : "Percent",
         "statistics" : [ {
           "statistic" : "average",
           "value" : 13.836
         } ]
       } ]
     }, {
       "metric" : {
         "dimensions" : [ {
           "name" : "clusterId",
           "value" : "83df17f1-d74c-11ec-a070-0255ac1000c3"
         } ],
         "metricName" : "gpuUtil",
         "namespace" : "PAAS.AGGR"
       },
       "dataPoints" : [ {
         "timestamp" : 1655193600000,
         "unit" : "Percent",
         "statistics" : [ {
           "statistic" : "average",
           "value" : -1
         } ]
       }, {
         "timestamp" : 1655197200000,
         "unit" : "Percent",
         "statistics" : [ {
           "statistic" : "average",
           "value" : -1
         } ]
       } ]
     }, {
       "metric" : {
         "dimensions" : [ {
           "name" : "clusterId",
           "value" : "83df17f1-d74c-11ec-a070-0255ac1000c3"
         } ],
         "metricName" : "gpuMemUsage",
         "namespace" : "PAAS.AGGR"
       },
       "dataPoints" : [ {
         "timestamp" : 1655193600000,
         "unit" : "Percent",
         "statistics" : [ {
           "statistic" : "average",
           "value" : -1
         } ]
       }, {
         "timestamp" : 1655197200000,
         "unit" : "Percent",
         "statistics" : [ {
           "statistic" : "average",
           "value" : -1
         } ]
       } ]
     }, {
       "metric" : {
         "dimensions" : [ {
           "name" : "clusterId",
           "value" : "83df17f1-d74c-11ec-a070-0255ac1000c3"
         } ],
         "metricName" : "npuUtil",
         "namespace" : "PAAS.AGGR"
       },
       "dataPoints" : [ {
         "timestamp" : 1655193600000,
         "unit" : "",
         "statistics" : [ {
           "statistic" : "average",
           "value" : -1
         } ]
       }, {
         "timestamp" : 1655197200000,
         "unit" : "",
         "statistics" : [ {
           "statistic" : "average",
           "value" : -1
         } ]
       } ]
     }, {
       "metric" : {
         "dimensions" : [ {
           "name" : "clusterId",
           "value" : "83df17f1-d74c-11ec-a070-0255ac1000c3"
         } ],
         "metricName" : "npuMemUsage",
         "namespace" : "PAAS.AGGR"
       },
       "dataPoints" : [ {
         "timestamp" : 1655193600000,
         "unit" : "",
         "statistics" : [ {
           "statistic" : "average",
           "value" : -1
         } ]
       }, {
         "timestamp" : 1655197200000,
         "unit" : "",
         "statistics" : [ {
           "statistic" : "average",
           "value" : -1
         } ]
       } ]
     }, {
       "metric" : {
         "dimensions" : [ {
           "name" : "clusterId",
           "value" : "83df17f1-d74c-11ec-a070-0255ac1000c3"
         } ],
         "metricName" : "diskAvailableCapacity",
         "namespace" : "PAAS.AGGR"
       },
       "dataPoints" : [ {
         "timestamp" : 1655193600000,
         "unit" : "Megabytes",
         "statistics" : [ {
           "statistic" : "average",
           "value" : 834383.4
         } ]
       }, {
         "timestamp" : 1655197200000,
         "unit" : "Megabytes",
         "statistics" : [ {
           "statistic" : "average",
           "value" : 834379.2
         } ]
       } ]
     }, {
       "metric" : {
         "dimensions" : [ {
           "name" : "clusterId",
           "value" : "83df17f1-d74c-11ec-a070-0255ac1000c3"
         } ],
         "metricName" : "diskCapacity",
         "namespace" : "PAAS.AGGR"
       },
       "dataPoints" : [ {
         "timestamp" : 1655193600000,
         "unit" : "Megabytes",
         "statistics" : [ {
           "statistic" : "average",
           "value" : 1105920
         } ]
       }, {
         "timestamp" : 1655197200000,
         "unit" : "Megabytes",
         "statistics" : [ {
           "statistic" : "average",
           "value" : 1105920
         } ]
       } ]
     }, {
       "metric" : {
         "dimensions" : [ {
           "name" : "clusterId",
           "value" : "83df17f1-d74c-11ec-a070-0255ac1000c3"
         } ],
         "metricName" : "diskUsedRate",
         "namespace" : "PAAS.AGGR"
       },
       "dataPoints" : [ {
         "timestamp" : 1655193600000,
         "unit" : "Percent",
         "statistics" : [ {
           "statistic" : "average",
           "value" : 24.553
         } ]
       }, {
         "timestamp" : 1655197200000,
         "unit" : "Percent",
         "statistics" : [ {
           "statistic" : "average",
           "value" : 24.553
         } ]
       } ]
     } ]
   }

**Status code: 404**

Not found.

.. code-block::

   {
     "error_code" : "ModelArts.50015001",
     "error_msg" : "pool not found"
   }

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
200         OK
404         Not found.
=========== ===========

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
