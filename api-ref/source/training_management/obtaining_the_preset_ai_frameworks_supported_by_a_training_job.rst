:original_name: ShowTrainingJobEngines.html

.. _ShowTrainingJobEngines:

Obtaining the Preset AI Frameworks Supported by a Training Job
==============================================================

Function
--------

This API is used to obtain the preset AI frameworks supported by a training job.

URI
---

GET /v2/{project_id}/training-job-engines

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                              |
   +============+===========+========+==========================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   +-----------+------------------------------------------------------------------------------+---------------------------------------+
   | Parameter | Type                                                                         | Description                           |
   +===========+==============================================================================+=======================================+
   | total     | Integer                                                                      | Total number of training job engines. |
   +-----------+------------------------------------------------------------------------------+---------------------------------------+
   | items     | Array of :ref:`items <en-us_topic_0000001910008144__response_items>` objects | List of engine specifications.        |
   +-----------+------------------------------------------------------------------------------+---------------------------------------+

.. _en-us_topic_0000001910008144__response_items:

.. table:: **Table 3** items

   +----------------+------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter      | Type                                                                         | Description                                                                                                              |
   +================+==============================================================================+==========================================================================================================================+
   | engine_id      | String                                                                       | Engine ID, for example, **caffe-1.0.0-python2.7**.                                                                       |
   +----------------+------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------+
   | engine_name    | String                                                                       | Engine name, for example, **Caffe**.                                                                                     |
   +----------------+------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------+
   | engine_version | String                                                                       | Engine version. Engines with the same name have multiple versions, for example, **Caffe-1.0.0-python2.7** of Python 2.7. |
   +----------------+------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------+
   | v1_compatible  | Boolean                                                                      | Whether the v1 compatibility mode is used.                                                                               |
   +----------------+------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------+
   | run_user       | String                                                                       | User UID started by default by the engine.                                                                               |
   +----------------+------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------+
   | image_info     | :ref:`image_info <en-us_topic_0000001910008144__response_image_info>` object | Engine information.                                                                                                      |
   +----------------+------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000001910008144__response_image_info:

.. table:: **Table 4** image_info

   ============= ====== ==========================================
   Parameter     Type   Description
   ============= ====== ==========================================
   cpu_image_url String Image with the matched CPU specifications.
   gpu_image_url String Image with the matched GPU flavors
   image_version String Image version.
   ============= ====== ==========================================

Example Requests
----------------

The following shows how to query all public engine specifications of a training job in (only part of the specifications are displayed because there are too many engines).

.. code-block:: text

   GET https://endpoint/v2/{project_id}/training-job-engines

Example Responses
-----------------

**Status code: 200**

ok

.. code-block::

   {
     "total" : 20,
     "items" : [ {
       "engine_id" : "caffe-1.0.0-python2.7",
       "engine_name" : "Caffe",
       "engine_version" : "caffe-1.0.0-python2.7",
       "v1_compatible" : true,
       "run_user" : "",
       "image_info" : {
         "cpu_image_url" : "modelarts-job-dev-image/caffe1-cpu-cp27:1.0.0",
         "gpu_image_url" : "modelarts-job-dev-image/caffe1-gpu-cuda8-cp27:1.0.0",
         "image_version" : "3.1.0"
       }
     }, {
       "engine_id" : "horovod-cp36-tf-1.16.2",
       "engine_name" : "Horovod",
       "engine_version" : "0.16.2-TF-1.13.1-python3.6",
       "v1_compatible" : true,
       "run_user" : "",
       "image_info" : {
         "cpu_image_url" : "modelarts-job-dev-image/tensorflow-gpu-cuda10-cp36-horovod0162:1.13.1",
         "gpu_image_url" : "modelarts-job-dev-image/tensorflow-gpu-cuda10-cp36-horovod0162:1.13.1",
         "image_version" : "3.2.1"
       }
     }, {
       "engine_id" : "horovod_0.20.0-tensorflow_2.1.0-cuda_10.1-py_3.7-ubuntu_18.04-x86_64",
       "engine_name" : "Horovod",
       "engine_version" : "horovod_0.20.0-tensorflow_2.1.0-cuda_10.1-py_3.7-ubuntu_18.04-x86_64",
       "v1_compatible" : false,
       "run_user" : "1102",
       "image_info" : {
         "cpu_image_url" : "aip/horovod_tensorflow:train",
         "gpu_image_url" : "aip/horovod_tensorflow:train",
         "image_version" : "horovod_0.20.0-tensorflow_2.1.0-cuda_10.1-py_3.7-ubuntu_18.04-x86_64-20210912152543-1e0838d"
       }
     }, "......", {
       "engine_id" : "tensorflow_2.1.0-cuda_10.1-py_3.7-ubuntu_18.04-x86_64",
       "engine_name" : "TensorFlow",
       "engine_version" : "tensorflow_2.1.0-cuda_10.1-py_3.7-ubuntu_18.04-x86_64",
       "v1_compatible" : false,
       "run_user" : "1102",
       "image_info" : {
         "cpu_image_url" : "aip/tensorflow_2_1:train",
         "gpu_image_url" : "aip/tensorflow_2_1:train",
         "image_version" : "tensorflow_2.1.0-cuda_10.1-py_3.7-ubuntu_18.04-x86_64-20210912152543-1e0838d"
       }
     }, {
       "engine_id" : "xgboost-sklearn-python3.6",
       "engine_name" : "XGBoost-Sklearn",
       "engine_version" : "XGBoost-0.80-Sklearn-0.18.1-python3.6",
       "v1_compatible" : true,
       "run_user" : "",
       "image_info" : {
         "cpu_image_url" : "modelarts-job-dev-image/python-train-py36:secure",
         "gpu_image_url" : "",
         "image_version" : "2.0.10-20211101113705"
       }
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
