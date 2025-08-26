:original_name: ShowModelEngineAndRuntime.html

.. _ShowModelEngineAndRuntime:

Obtaining the Model Runtime
===========================

Function
--------

This API is used to obtain the AI engine and runtime of models.

URI
---

GET /v1/{project_id}/models/ai-engine-runtimes

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+---------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                     |
   +============+===========+========+=================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID <modelarts_03_0147>`. |
   +------------+-----------+--------+---------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------+-----------+--------+-----------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                         |
   +===========+===========+========+=====================================================================================================+
   | limit     | No        | String | Number of items displayed on each page                                                              |
   +-----------+-----------+--------+-----------------------------------------------------------------------------------------------------+
   | offset    | No        | String | Offset, which is the position where the query starts. The value must be greater than or equal to 0. |
   +-----------+-----------+--------+-----------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   ============ ========= ====== ===========
   Parameter    Mandatory Type   Description
   ============ ========= ====== ===========
   X-Auth-Token Yes       String User token.
   ============ ========= ====== ===========

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type                                                                                                                                              | Description                                                                                                                                |
   +=================+===================================================================================================================================================+============================================================================================================================================+
   | count           | Integer                                                                                                                                           | Total number of records that meet the search criteria when no pagination is performed                                                      |
   +-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | total_count     | Integer                                                                                                                                           | Number of records in the query result. If **offset** and **limit** are not configured, the values of **count** and **total** are the same. |
   +-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | engine_runtimes | Array of :ref:`EngineAndRuntimesResponse <en-us_topic_0000002340898614__en-us_topic_0000002055164110_response_engineandruntimesresponse>` objects | Engine runtime environment                                                                                                                 |
   +-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002340898614__en-us_topic_0000002055164110_response_engineandruntimesresponse:

.. table:: **Table 5** EngineAndRuntimesResponse

   +-----------------------+-----------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                                                  | Description                                                                          |
   +=======================+=======================================================================================================================+======================================================================================+
   | ai_engine             | String                                                                                                                | AI engine type. The options are as follows:                                          |
   |                       |                                                                                                                       |                                                                                      |
   |                       |                                                                                                                       | -  **TensorFlow**                                                                    |
   |                       |                                                                                                                       |                                                                                      |
   |                       |                                                                                                                       | -  **PyTorch**                                                                       |
   |                       |                                                                                                                       |                                                                                      |
   |                       |                                                                                                                       | -  **MindSpore**                                                                     |
   |                       |                                                                                                                       |                                                                                      |
   |                       |                                                                                                                       | -  **XGBoost**                                                                       |
   |                       |                                                                                                                       |                                                                                      |
   |                       |                                                                                                                       | -  **Scikit_Learn**                                                                  |
   |                       |                                                                                                                       |                                                                                      |
   |                       |                                                                                                                       | -  **Spark_MLlib**                                                                   |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------+
   | runtimes              | Array of strings                                                                                                      | Runtime image, for example, **pytorch_1.8.0-cuda_10.2-py_3.7-ubuntu_18.04-x86_64**   |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------+
   | request_mode          | Array of strings                                                                                                      | Request mode. The AI engine supports synchronous or asynchronous real-time services. |
   |                       |                                                                                                                       |                                                                                      |
   |                       |                                                                                                                       | -  **sync**: synchronous real-time service                                           |
   |                       |                                                                                                                       |                                                                                      |
   |                       |                                                                                                                       | -  **async**: asynchronous real-time service                                         |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------+
   | accelerators          | Array of :ref:`Accelerator <en-us_topic_0000002340898614__en-us_topic_0000002055164110_response_accelerator>` objects | Accelerator cards that can be used by the AI engine.                                 |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------+
   | arch                  | Array of strings                                                                                                      | AI engine architecture. The options are as follows:                                  |
   |                       |                                                                                                                       |                                                                                      |
   |                       |                                                                                                                       | -  **x86_64**                                                                        |
   |                       |                                                                                                                       |                                                                                      |
   |                       |                                                                                                                       | -  **aarch64**                                                                       |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------+
   | status_list           | Array of strings                                                                                                      | AI engine status. The options are as follows:                                        |
   |                       |                                                                                                                       |                                                                                      |
   |                       |                                                                                                                       | -  **normal**: The AI engine is normal.                                              |
   |                       |                                                                                                                       |                                                                                      |
   |                       |                                                                                                                       | -  **deleted**: The AI engine is deleted.                                            |
   |                       |                                                                                                                       |                                                                                      |
   |                       |                                                                                                                       | -  **deleting**: The AI engine is being deleted.                                     |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------+
   | image_source          | Array of strings                                                                                                      | Image source. The options are as follows:                                            |
   |                       |                                                                                                                       |                                                                                      |
   |                       |                                                                                                                       | -  **base_image**                                                                    |
   |                       |                                                                                                                       |                                                                                      |
   |                       |                                                                                                                       | -  **uniform_image**                                                                 |
   +-----------------------+-----------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------+

.. _en-us_topic_0000002340898614__en-us_topic_0000002055164110_response_accelerator:

.. table:: **Table 6** Accelerator

   +------------------------+-----------------------+----------------------------------------------------+
   | Parameter              | Type                  | Description                                        |
   +========================+=======================+====================================================+
   | type                   | String                | Accelerator card type. The options are as follows: |
   |                        |                       |                                                    |
   |                        |                       | -  **npu**                                         |
   |                        |                       |                                                    |
   |                        |                       | -  **gpu**                                         |
   |                        |                       |                                                    |
   |                        |                       | -  **none**                                        |
   +------------------------+-----------------------+----------------------------------------------------+
   | name                   | String                | Accelerator card name, for example, **SNT9B**.     |
   +------------------------+-----------------------+----------------------------------------------------+
   | cuda_version           | String                | CUDA driver version.                               |
   +------------------------+-----------------------+----------------------------------------------------+
   | driver_version_section | String                | Driver version set.                                |
   +------------------------+-----------------------+----------------------------------------------------+

**Status code: 401**

.. table:: **Table 7** Response body parameters

   ========== ====== =========================
   Parameter  Type   Description
   ========== ====== =========================
   error_code String Error codes of ModelArts.
   error_msg  String Error message.
   ========== ====== =========================

**Status code: 403**

.. table:: **Table 8** Response body parameters

   ========== ====== =========================
   Parameter  Type   Description
   ========== ====== =========================
   error_code String Error codes of ModelArts.
   error_msg  String Error message.
   ========== ====== =========================

**Status code: 404**

.. table:: **Table 9** Response body parameters

   ========== ====== =========================
   Parameter  Type   Description
   ========== ====== =========================
   error_code String Error codes of ModelArts.
   error_msg  String Error message.
   ========== ====== =========================

Example Requests
----------------

.. code-block:: text

   GET https://{endpoint}/v1/{project_id}/models/ai-engine-runtimes

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "count" : 4,
     "total_count" : 4,
     "engine_runtimes" : [ {
       "ai_engine" : "TensorFlow",
       "runtimes" : [ "tf1.13-python3.6-cpu", "tf1.13-python3.6-gpu", "tf1.13-python3.7-cpu", "tf1.13-python3.7-gpu", "python3.6", "tf1.13-python3.7-aiflow-gpu", "tf1.13-python3.7-gpu-async", "tensorflow_2.1.0-cuda_10.1-py_3.7-ubuntu_18.04-x86_64", "tensorflow_2.6.0-cuda_11.2-py_3.7-ubuntu_18.04-x86_64", "tensorflow_1.15.5-cuda_11.4-py_3.8-ubuntu_20.04-x86_64" ],
       "request_mode" : [ "sync", "sync", "sync", "sync", "sync", "sync", "async", "sync", "sync", "sync" ],
       "accelerators" : [ {
         "type" : "none"
       }, {
         "type" : "gpu",
         "cuda_version" : "cuda 10.2"
       }, {
         "type" : "none"
       }, {
         "type" : "gpu",
         "cuda_version" : "cuda 10.2"
       }, {
         "type" : "none"
       }, {
         "type" : "gpu",
         "cuda_version" : "cuda 10.2"
       }, {
         "type" : "gpu",
         "cuda_version" : "cuda 10.2"
       }, {
         "type" : "none"
       }, {
         "type" : "none"
       }, {
         "type" : "none"
       } ],
       "arch" : [ "x86_64", "x86_64", "x86_64", "x86_64", "x86_64", "x86_64", "x86_64", "x86_64", "x86_64", "x86_64" ],
       "status_list" : [ "normal", "normal", "normal", "normal", "normal", "normal", "normal", "normal", "normal", "normal" ],
       "image_source" : [ "base_image", "base_image", "base_image", "base_image", "base_image", "base_image", "base_image", "uniform_image", "uniform_image", "uniform_image" ]
     }, {
       "ai_engine" : "PyTorch",
       "runtimes" : [ "python3.6", "python3.7", "pytorch1.4-python3.7", "pytorch_1.11.0-cann_7.0.1-py_3.9-euler_2.10.7-aarch64-snt9b", "pytorch_1.8.0-cuda_10.2-py_3.7-ubuntu_18.04-x86_64", "pytorch_1.8.2-cuda_11.1-py_3.7-ubuntu_18.04-x86_64" ],
       "request_mode" : [ "sync", "sync", "sync", "sync", "sync", "sync" ],
       "accelerators" : [ {
         "type" : "none"
       }, {
         "type" : "none"
       }, {
         "type" : "none"
       }, {
         "type" : "npu",
         "name" : "SNT9",
         "driver_version_section" : "C8x"
       }, {
         "type" : "none"
       }, {
         "type" : "none"
       } ],
       "arch" : [ "x86_64", "x86_64", "x86_64", "aarch64", "x86_64", "x86_64" ],
       "status_list" : [ "normal", "normal", "normal", "normal", "normal", "normal" ],
       "image_source" : [ "base_image", "base_image", "base_image", "uniform_image", "uniform_image", "uniform_image" ]
     }, {
       "ai_engine" : "MindSpore",
       "runtimes" : [ "mindspore_1.9.0-cann_6.0.1-py_3.7-euler_2.9.9-x86_64-snt3p-300i", "mindspore_1.7.0-cuda_10.1-py_3.7-ubuntu_18.04-x86_64", "mindspore_1.2.0-py_3.7-cuda_10.1-ubuntu_18.04-x86_64" ],
       "request_mode" : [ "sync", "sync", "sync" ],
       "accelerators" : [ {
         "type" : "none"
       }, {
         "type" : "none"
       }, {
         "type" : "none"
       } ],
       "arch" : [ "x86_64", "x86_64", "x86_64" ],
       "status_list" : [ "normal", "normal", "normal" ],
       "image_source" : [ "uniform_image", "uniform_image", "uniform_image" ]
     }, {
       "ai_engine" : "Custom",
       "runtimes" : [ ],
       "request_mode" : [ ],
       "accelerators" : [ ],
       "arch" : [ ],
       "status_list" : [ ],
       "image_source" : [ ]
     } ]
   }

Status Codes
------------

=========== ============
Status Code Description
=========== ============
200         OK
401         Unauthorized
403         Forbidden
404         Not Found
=========== ============

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
