.. _modelarts_03_0151:

Querying Monitoring Information About Resource Pool Nodes
=========================================================

Function
--------

This API is used to query monitoring information about resource pool nodes.

URI
---

GET /v1/{project_id}/pools/{pool_id}/nodes/{node_ip}/metric-statistic

:ref:`Table 1 <modelarts_03_0151__en-us_topic_0188079989_table4442765616454>` describes the required parameters.

.. _modelarts_03_0151__en-us_topic_0188079989_table4442765616454:

.. table:: **Table 1** Parameter description

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                           |
   +============+===========+========+=======================================================================================================+
   | project_id | Yes       | String | Project ID                                                                                            |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------+
   | pool_id    | Yes       | String | ID of a dedicated resource pool                                                                       |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------+
   | node_ip    | Yes       | String | IP address of a resource pool node, which is obtained from the response of the pool details query API |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------+

Request Body
------------

:ref:`Table 2 <modelarts_03_0151__en-us_topic_0188079989_table87520312215>` describes the request parameters.

.. _modelarts_03_0151__en-us_topic_0188079989_table87520312215:

.. table:: **Table 2** Parameter description

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                            |
   +=================+=================+=================+========================================================================================================================================================+
   | metrics         | No              | String          | Metrics to be queried. Separate metrics by commas (,), for example, **CpuUsage,MemUsage**. If this parameter is left blank, all metrics are queried.   |
   |                 |                 |                 |                                                                                                                                                        |
   |                 |                 |                 | Options:                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                        |
   |                 |                 |                 | -  **CpuUsage**: CPU usage                                                                                                                             |
   |                 |                 |                 | -  **MemUsage**: memory usage                                                                                                                          |
   |                 |                 |                 | -  **DiskReadRate**: disk read rate                                                                                                                    |
   |                 |                 |                 | -  **DiskWriteRate**: disk write rate                                                                                                                  |
   |                 |                 |                 | -  **RecvBytesRate**: network receiving rate                                                                                                           |
   |                 |                 |                 | -  **SendBytesRate**: network sending rate                                                                                                             |
   |                 |                 |                 | -  **GpuUtil**: GPU usage                                                                                                                              |
   |                 |                 |                 | -  **GpuMemUsage**: GPU memory usage                                                                                                                   |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | statistic_type  | No              | String          | Metric statistics method, indicating whether to collect metric statistics based on a single GPU. This parameter applies only to GPU metric statistics. |
   |                 |                 |                 |                                                                                                                                                        |
   |                 |                 |                 | -  **all**: Obtain the average value of the metric.                                                                                                    |
   |                 |                 |                 | -  **each**: Obtain the metric monitoring information about each GPU.                                                                                  |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Body
-------------

:ref:`Table 3 <modelarts_03_0151__en-us_topic_0188079989_table1414514116749>` describes the response parameters.

.. _modelarts_03_0151__en-us_topic_0188079989_table1414514116749:

.. table:: **Table 3** Parameter description

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                         |
   +=======================+=======================+=====================================================================================================================================================+
   | error_message         | String                | Error message of a failed API call.                                                                                                                 |
   |                       |                       |                                                                                                                                                     |
   |                       |                       | This parameter is not included when the API call succeeds.                                                                                          |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | error_code            | String                | Indicates the error code when the API fails to be called. Error code of a failed API call. For details, see :ref:`Error Codes <modelarts_03_0095>`. |
   |                       |                       |                                                                                                                                                     |
   |                       |                       | This parameter is not included when the API call succeeds.                                                                                          |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | metrics               | Json Array            | Metric monitoring details. For details, see :ref:`Table 4 <modelarts_03_0151__en-us_topic_0188079989_table8361164171810>`.                          |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | interval              | Integer               | Query interval, in minutes.                                                                                                                         |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

.. _modelarts_03_0151__en-us_topic_0188079989_table8361164171810:

.. table:: **Table 4** metrics data structure

   +-----------+------------+---------------------------------------------------------------------------+
   | Parameter | Type       | Description                                                               |
   +===========+============+===========================================================================+
   | metric    | String     | Monitoring metrics                                                        |
   +-----------+------------+---------------------------------------------------------------------------+
   | value     | Json Array | Sequence of the obtained metric value. The element is of the String type. |
   +-----------+------------+---------------------------------------------------------------------------+

Samples
-------

The following example queries monitoring information about node **192.168.1.1** in the dedicated resource pool **poolabcd**.

-  Sample request

   .. code-block::

      GET    https://endpoint/v1/{project_id}/pools/poolabcd/nodes/192.168.1.1/metric-statistic

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
