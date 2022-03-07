ModelArts Metrics
=================

Description
-----------

The cloud service platform provides Cloud Eye to help you better understand the status of your ModelArts real-time services and models. You can use Cloud Eye to automatically monitor your ModelArts real-time services and models in real time and manage alarms and notifications, so that you can keep track of performance metrics of ModelArts and models.

Namespace
---------

SYS.ModelArts

Monitoring Metrics
------------------



.. _modelarts_23_0187__en-us_topic_0198064686_table3293914123812:

.. table:: **Table 1** ModelArts metrics

   +--------------------------------------------------------------------+------------------+-------------------+-------------+------------------+------------+
   | Metric ID                                                          | Metric Name      | Meaning           | Value Range | Measurement      | Monitoring |
   |                                                                    |                  |                   |             | Object &         | Interval   |
   |                                                                    |                  |                   |             | Dimension        |            |
   +====================================================================+==================+===================+=============+==================+============+
   | cpu_usage                                                          | CPU Usage        | CPU usage of      | ≥ 0%        | Measurement      | 1 minute   |
   |                                                                    |                  | ModelArts         |             | object:          |            |
   |                                                                    |                  |                   |             |                  |            |
   |                                                                    |                  | Unit: %           |             | ModelArts models |            |
   |                                                                    |                  |                   |             |                  |            |
   |                                                                    |                  |                   |             | Dimension:       |            |
   |                                                                    |                  |                   |             | model_id         |            |
   +--------------------------------------------------------------------+------------------+-------------------+-------------+------------------+------------+
   | mem_usage                                                          | Memory Usage     | Memory usage of   | ≥ 0%        | Measurement      | 1 minute   |
   |                                                                    |                  | ModelArts         |             | object:          |            |
   |                                                                    |                  |                   |             |                  |            |
   |                                                                    |                  | Unit: %           |             | ModelArts models |            |
   |                                                                    |                  |                   |             |                  |            |
   |                                                                    |                  |                   |             | Dimension:       |            |
   |                                                                    |                  |                   |             | model_id         |            |
   +--------------------------------------------------------------------+------------------+-------------------+-------------+------------------+------------+
   | gpu_util                                                           | GPU Usage        | GPU usage of      | ≥ 0%        | Measurement      | 1 minute   |
   |                                                                    |                  | ModelArts         |             | object:          |            |
   |                                                                    |                  |                   |             |                  |            |
   |                                                                    |                  | Unit: %           |             | ModelArts models |            |
   |                                                                    |                  |                   |             |                  |            |
   |                                                                    |                  |                   |             | Dimension:       |            |
   |                                                                    |                  |                   |             | model_id         |            |
   +--------------------------------------------------------------------+------------------+-------------------+-------------+------------------+------------+
   | gpu_mem_usage                                                      | GPU Memory Usage | GPU memory usage  | ≥ 0%        | Measurement      | 1 minute   |
   |                                                                    |                  | of ModelArts      |             | object:          |            |
   |                                                                    |                  |                   |             |                  |            |
   |                                                                    |                  | Unit: %           |             | ModelArts models |            |
   |                                                                    |                  |                   |             |                  |            |
   |                                                                    |                  |                   |             | Dimension:       |            |
   |                                                                    |                  |                   |             | model_id         |            |
   +--------------------------------------------------------------------+------------------+-------------------+-------------+------------------+------------+
   | successfully_called_times                                          | Number of        | Times that        | ≥Count/min  | Measurement      | 1 minute   |
   |                                                                    | Successful Calls | ModelArts has     |             | object:          |            |
   |                                                                    |                  | been successfully |             |                  |            |
   |                                                                    |                  | called            |             | ModelArts models |            |
   |                                                                    |                  |                   |             |                  |            |
   |                                                                    |                  | Unit: Times/min   |             | ModelArts        |            |
   |                                                                    |                  |                   |             | real-time        |            |
   |                                                                    |                  |                   |             | services         |            |
   |                                                                    |                  |                   |             |                  |            |
   |                                                                    |                  |                   |             | Dimension:       |            |
   |                                                                    |                  |                   |             | model_id,        |            |
   |                                                                    |                  |                   |             | service_id       |            |
   +--------------------------------------------------------------------+------------------+-------------------+-------------+------------------+------------+
   | failed_called_times                                                | Number of Failed | Times that        | ≥Count/min  | Measurement      | 1 minute   |
   |                                                                    | Calls            | ModelArts failed  |             | object:          |            |
   |                                                                    |                  | to be called      |             |                  |            |
   |                                                                    |                  |                   |             | ModelArts models |            |
   |                                                                    |                  | Unit: Times/min   |             |                  |            |
   |                                                                    |                  |                   |             | ModelArts        |            |
   |                                                                    |                  |                   |             | real-time        |            |
   |                                                                    |                  |                   |             | services         |            |
   |                                                                    |                  |                   |             |                  |            |
   |                                                                    |                  |                   |             | Dimension:       |            |
   |                                                                    |                  |                   |             | model_id,        |            |
   |                                                                    |                  |                   |             | service_id       |            |
   +--------------------------------------------------------------------+------------------+-------------------+-------------+------------------+------------+
   | total_called_times                                                 | API Calls        | Times that        | ≥Count/min  | Measurement      | 1 minute   |
   |                                                                    |                  | ModelArts is      |             | object:          |            |
   |                                                                    |                  | called            |             |                  |            |
   |                                                                    |                  |                   |             | ModelArts models |            |
   |                                                                    |                  | Unit: Times/min   |             |                  |            |
   |                                                                    |                  |                   |             | ModelArts        |            |
   |                                                                    |                  |                   |             | real-time        |            |
   |                                                                    |                  |                   |             | services         |            |
   |                                                                    |                  |                   |             |                  |            |
   |                                                                    |                  |                   |             | Dimension:       |            |
   |                                                                    |                  |                   |             | model_id,        |            |
   |                                                                    |                  |                   |             | service_id       |            |
   +--------------------------------------------------------------------+------------------+-------------------+-------------+------------------+------------+
   | If a measurement object has multiple measurement                   |                  |                   |             |                  |            |
   | dimensions, all the measurement dimensions are                     |                  |                   |             |                  |            |
   | mandatory when you use an API to query monitoring                  |                  |                   |             |                  |            |
   | metrics.                                                           |                  |                   |             |                  |            |
   |                                                                    |                  |                   |             |                  |            |
   | - The following provides an example of using the multi-dimensional |                  |                   |             |                  |            |
   |   **dim** to query a single monitoring metric:                     |                  |                   |             |                  |            |
   |   dim.0=service_id,530cd6b0-86d7-4818-837f-935f6a27414d&           |                  |                   |             |                  |            |
   |   dim.1=model_id,3773b058-5b4f-4366-9035-9bbd9964714a              |                  |                   |             |                  |            |
   |                                                                    |                  |                   |             |                  |            |
   | - The following provides an example of using the multi-dimensional |                  |                   |             |                  |            |
   |   **dim** to query monitoring metrics in batches:                  |                  |                   |             |                  |            |
   |                                                                    |                  |                   |             |                  |            |
   |    "dimensions":                                                   |                  |                   |             |                  |            |
   |    [                                                               |                  |                   |             |                  |            |
   |    {                                                               |                  |                   |             |                  |            |
   |    "name": "service_id",                                           |                  |                   |             |                  |            |
   |    "value": "530cd6b0-86d7-4818-8cd6b0-37f-935f6a27414d"           |                  |                   |             |                  |            |
   |    }                                                               |                  |                   |             |                  |            |
   |    {                                                               |                  |                   |             |                  |            |
   |    "name": "model_id",                                             |                  |                   |             |                  |            |
   |    "value": "3773b058-5b4f-4366-9035-9bbd9964714a"                 |                  |                   |             |                  |            |
   |    }                                                               |                  |                   |             |                  |            |
   |    ],                                                              |                  |                   |             |                  |            |
   +--------------------------------------------------------------------+------------------+-------------------+-------------+------------------+------------+

Dimensions
----------



.. _modelarts_23_0187__en-us_topic_0198064686_table130310173915:

.. table:: **Table 2** Dimension description

   ========== ====================
   Key        Value
   ========== ====================
   service_id Real-time service ID
   model_id   Model ID
   ========== ====================
