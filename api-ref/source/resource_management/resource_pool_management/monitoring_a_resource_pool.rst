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

   ========== ========= ====== ===========================================
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========================================
   project_id Yes       String Project ID.
   pool_name  Yes       String Automatically generated resource pool name.
   ========== ========= ====== ===========================================

.. table:: **Table 2** Query Parameters

   ========== ========= ====== ===========================
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========================
   time_range No        String Default value: **-1.-1.60**
   statistics No        String Default value: **maximum**
   period     No        String Default value: **60**
   ========== ========= ====== ===========================

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------+----------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | Parameter | Type                                                                             | Description                                                                   |
   +===========+==================================================================================+===============================================================================+
   | metrics   | Array of :ref:`metrics <en-us_topic_0000002080257337__response_metrics>` objects | Metric list. The value is a JSON array that contains a maximum of 20 objects. |
   +-----------+----------------------------------------------------------------------------------+-------------------------------------------------------------------------------+

.. _en-us_topic_0000002080257337__response_metrics:

.. table:: **Table 4** metrics

   +------------+----------------------------------------------------------------------------------------+-------------+
   | Parameter  | Type                                                                                   | Description |
   +============+========================================================================================+=============+
   | metric     | :ref:`metric <en-us_topic_0000002080257337__response_metric>` object                   | Metrics     |
   +------------+----------------------------------------------------------------------------------------+-------------+
   | dataPoints | Array of :ref:`dataPoints <en-us_topic_0000002080257337__response_datapoints>` objects | Key metrics |
   +------------+----------------------------------------------------------------------------------------+-------------+

.. _en-us_topic_0000002080257337__response_metric:

.. table:: **Table 5** metric

   +-----------------------+----------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                   | Description                                                                             |
   +=======================+========================================================================================+=========================================================================================+
   | dimensions            | Array of :ref:`dimensions <en-us_topic_0000002080257337__response_dimensions>` objects | Dimensions                                                                              |
   +-----------------------+----------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+
   | metricName            | String                                                                                 | Metric name. Options:                                                                   |
   |                       |                                                                                        |                                                                                         |
   |                       |                                                                                        | -  **cpuUsage**: CPU usage                                                              |
   |                       |                                                                                        |                                                                                         |
   |                       |                                                                                        | -  **memUsedRate**: memory usage                                                        |
   |                       |                                                                                        |                                                                                         |
   |                       |                                                                                        | -  **gpuUtil**: GPU usage                                                               |
   |                       |                                                                                        |                                                                                         |
   |                       |                                                                                        | -  **gpuMemUsage**: used GPU memory                                                     |
   |                       |                                                                                        |                                                                                         |
   |                       |                                                                                        | -  **npuUtil**: NPU usage                                                               |
   |                       |                                                                                        |                                                                                         |
   |                       |                                                                                        | -  **npuMemUsage**: used NPU memory                                                     |
   |                       |                                                                                        |                                                                                         |
   |                       |                                                                                        | -  **diskCapacity**: disk capacity                                                      |
   |                       |                                                                                        |                                                                                         |
   |                       |                                                                                        | -  **diskAvailableCapacity**: available disk capacity                                   |
   |                       |                                                                                        |                                                                                         |
   |                       |                                                                                        | -  **diskUsedRate**: disk usage                                                         |
   +-----------------------+----------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+
   | namespace             | String                                                                                 | Metric namespace. Options:                                                              |
   |                       |                                                                                        |                                                                                         |
   |                       |                                                                                        | -  **PAAS.CONTAINER**: namespace of component, instance, process, and container metrics |
   |                       |                                                                                        |                                                                                         |
   |                       |                                                                                        | -  **PAAS.NODE**: namespace of host, network, disk, and file system metrics             |
   |                       |                                                                                        |                                                                                         |
   |                       |                                                                                        | -  **PAAS.SLA**: namespace of SLA metrics                                               |
   |                       |                                                                                        |                                                                                         |
   |                       |                                                                                        | -  **PAAS.AGGR**: namespace of cluster metrics                                          |
   |                       |                                                                                        |                                                                                         |
   |                       |                                                                                        | -  **CUSTOMMETRICS**: default namespace of custom metrics                               |
   +-----------------------+----------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+

.. _en-us_topic_0000002080257337__response_dimensions:

.. table:: **Table 6** dimensions

   ========= ====== ======================
   Parameter Type   Description
   ========= ====== ======================
   name      String Metric dimension name
   value     String Metric dimension value
   ========= ====== ======================

.. _en-us_topic_0000002080257337__response_datapoints:

.. table:: **Table 7** dataPoints

   +------------+----------------------------------------------------------------------------------------+----------------------------+
   | Parameter  | Type                                                                                   | Description                |
   +============+========================================================================================+============================+
   | timestamp  | Integer                                                                                | Timestamp                  |
   +------------+----------------------------------------------------------------------------------------+----------------------------+
   | unit       | String                                                                                 | Time series unit           |
   +------------+----------------------------------------------------------------------------------------+----------------------------+
   | statistics | Array of :ref:`statistics <en-us_topic_0000002080257337__response_statistics>` objects | List of statistical values |
   +------------+----------------------------------------------------------------------------------------+----------------------------+

.. _en-us_topic_0000002080257337__response_statistics:

.. table:: **Table 8** statistics

   +-----------------------+-----------------------+--------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                  |
   +=======================+=======================+==============================================================+
   | statistic             | String                | Statistical mode. Options:                                   |
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
