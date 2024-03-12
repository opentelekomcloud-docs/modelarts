:original_name: ListImage.html

.. _ListImage:

Querying Supported Images
=========================

Function
--------

This API is used to query all images by page based on specified conditions.

Constraints
-----------

None

URI
---

GET /v1/{project_id}/images

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+---------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                     |
   +============+===========+========+=================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID <modelarts_03_0147>`. |
   +------------+-----------+--------+---------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +--------------+-----------+---------+------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type    | Description                                                                                          |
   +==============+===========+=========+======================================================================================================+
   | limit        | No        | Integer | Number of records on each page.                                                                      |
   +--------------+-----------+---------+------------------------------------------------------------------------------------------------------+
   | name         | No        | String  | Image name.                                                                                          |
   +--------------+-----------+---------+------------------------------------------------------------------------------------------------------+
   | namespace    | No        | String  | Image organization.                                                                                  |
   +--------------+-----------+---------+------------------------------------------------------------------------------------------------------+
   | offset       | No        | Integer | Start offset of the records on each page.                                                            |
   +--------------+-----------+---------+------------------------------------------------------------------------------------------------------+
   | sort_dir     | No        | String  | Sorting order. The options are **ASC** (ascending order) and **DESC** (descending order).            |
   +--------------+-----------+---------+------------------------------------------------------------------------------------------------------+
   | sort_key     | No        | String  | Sorting fields. Separate multiple fields with commas (,).                                            |
   +--------------+-----------+---------+------------------------------------------------------------------------------------------------------+
   | type         | No        | String  | Image type. Options: - **BUILD_IN**: built-in system image.- **DEDICATED**: image saved by the user. |
   +--------------+-----------+---------+------------------------------------------------------------------------------------------------------+
   | workspace_id | No        | String  | Workspace ID. If no workspaces are available, the default value is **0**.                            |
   +--------------+-----------+---------+------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------+-----------------------------------------------------------+--------------------------------+
   | Parameter | Type                                                      | Description                    |
   +===========+===========================================================+================================+
   | current   | Integer                                                   | Current page                   |
   +-----------+-----------------------------------------------------------+--------------------------------+
   | data      | Array of :ref:`Image <listimage__response_image>` objects | Data                           |
   +-----------+-----------------------------------------------------------+--------------------------------+
   | pages     | Integer                                                   | Total pages                    |
   +-----------+-----------------------------------------------------------+--------------------------------+
   | size      | Integer                                                   | Number of records on each page |
   +-----------+-----------------------------------------------------------+--------------------------------+
   | total     | Long                                                      | Total records                  |
   +-----------+-----------------------------------------------------------+--------------------------------+

.. _listimage__response_image:

.. table:: **Table 4** Image

   +-----------+--------+----------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                        |
   +===========+========+====================================================================================================+
   | id        | String | Image ID                                                                                           |
   +-----------+--------+----------------------------------------------------------------------------------------------------+
   | name      | String | Image name.                                                                                        |
   +-----------+--------+----------------------------------------------------------------------------------------------------+
   | swr_path  | String | SWR image address                                                                                  |
   +-----------+--------+----------------------------------------------------------------------------------------------------+
   | type      | String | Image type. Options: - **BUILD_IN**: built-in system image- **DEDICATED**: image saved by the user |
   +-----------+--------+----------------------------------------------------------------------------------------------------+

Example Requests
----------------

None

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "current" : 0,
     "data" : [ {
       "arch" : "x86_64",
       "description" : "CPU and GPU general algorithm development and training, preconfigured with AI engine PyTorch1.4",
       "dev_services" : [ "NOTEBOOK", "SSH" ],
       "id" : "e1a07296-22a8-4f05-8bc8-e936c8e54099",
       "name" : "pytorch1.4-cuda10.1-cudnn7-ubuntu18.04",
       "resource_categories" : [ "CPU", "GPU" ],
       "status" : "ACTIVE",
       "swr_path" : ".xxxx.com/atelier/notebook2.0-pytorch-1.4-kernel-cp37:3.3.3-B003-20211220",
       "tag" : "3.3.3-B003-20211220",
       "type" : "BUILD_IN",
       "update_at" : 1632415390765,
       "workspace_id" : "0"
     }, {
       "arch" : "x86_64",
       "description" : "CPU and GPU general algorithm development and training, preconfigured with AI engine TensorFlow2.1",
       "dev_services" : [ "NOTEBOOK", "SSH" ],
       "id" : "e1a07296-22a8-4f05-8bc8-e936c8e54100",
       "name" : "tensorflow2.1-cuda10.1-cudnn7-ubuntu18.04",
       "resource_categories" : [ "CPU", "GPU" ],
       "status" : "ACTIVE",
       "swr_path" : ".xxxx.com/atelier/notebook2.0-tensorflow-2.1-kernel-cp37:3.3.3-B005-20211227",
       "tag" : "3.3.3-B005-20211227",
       "type" : "BUILD_IN",
       "update_at" : 1632415555548,
       "workspace_id" : "0"
     }, {
       "arch" : "aarch64",
       "description" : "notebook2.0-mul-kernel-arm-ascend-cp37",
       "dev_services" : [ "NOTEBOOK", "SSH" ],
       "id" : "1d925a2e-dd3f-4f7c-ba15-1e5cb23a6b25",
       "name" : "notebook2.0-mul-kernel-arm-ascend-cp37",
       "resource_categories" : [ ],
       "swr_path" : ".xxxx.com/atelier/notebook2.0-mul-kernel-arm-ascend-cp37:3.3.2-c79_release_v3",
       "tag" : "3.3.2-c79_release_v3",
       "type" : "BUILD_IN",
       "workspace_id" : "0"
     }, {
       "arch" : "x86_64",
       "description" : "GPU algorithm development and training, preconfigured with the AI engine MindSpore-GPU",
       "dev_services" : [ "NOTEBOOK", "SSH" ],
       "id" : "89de30ec-6871-4f22-84af-be37ef28335d",
       "name" : "mindspore1.2.0-cuda10.1-cudnn7-ubuntu18.04",
       "resource_categories" : [ "GPU" ],
       "status" : "ACTIVE",
       "swr_path" : ".xxxx.com/atelier/notebook2.0-mindspore-kernel-gpu-cp37:3.3.3-B003-20211220",
       "tag" : "3.3.3-B003-20211220",
       "type" : "BUILD_IN",
       "update_at" : 1632502757168,
       "workspace_id" : "0"
     }, {
       "arch" : "x86_64",
       "description" : "CPU algorithm development and training, preconfigured with the AI engine MindSpore-CPU",
       "dev_services" : [ "NOTEBOOK", "SSH" ],
       "id" : "65f636a0-56cf-49df-b941-7d2a07ba8c8c",
       "name" : "mindspore1.2.0-openmpi2.1.1-ubuntu18.04",
       "resource_categories" : [ "CPU" ],
       "status" : "ACTIVE",
       "swr_path" : ".xxxx.com/atelier/notebook2.0-mindspore-kernel-cpu-cp37:3.3.3-B003-20211220",
       "tag" : "3.3.3-B003-20211220",
       "type" : "BUILD_IN",
       "update_at" : 1632415234204,
       "workspace_id" : "0"
     }, {
       "arch" : "x86_64",
       "description" : "CPU algorithm development and training, including the MLStudio tool for graphical ML algorithm development, and preconfigured PySpark 2.3.2",
       "dev_services" : [ "NOTEBOOK", "SSH" ],
       "id" : "0e5f9a41-c9c2-4d9a-a190-4e1b17a7782f",
       "name" : "mlstudio-pyspark2.3.2-ubuntu16.04",
       "resource_categories" : [ "CPU" ],
       "status" : "ACTIVE",
       "swr_path" : ".xxxx.com/atelier/notebook2.0-mlstudio-cp36:3.3.1.9",
       "tag" : "3.3.1.9",
       "type" : "BUILD_IN",
       "update_at" : 1632415063632,
       "workspace_id" : "0"
     }, {
       "arch" : "x86_64",
       "description" : "CPU algorithm development and training, including the MLStudio tool for graphical ML algorithm development, and preconfigured PySpark 2.4.5",
       "dev_services" : [ "NOTEBOOK" ],
       "id" : "0b2d0728-4c01-11ec-994f-001a7dda7111",
       "name" : "mlstudio-pyspark2.4.5-ubuntu18.04",
       "resource_categories" : [ "CPU" ],
       "status" : "ACTIVE",
       "swr_path" : ".xxxx.com/atelier/notebook2.0-mlstudio-cp37:3.3.3-B003-20211220",
       "tag" : "3.3.3-B003-20211220",
       "type" : "BUILD_IN",
       "workspace_id" : "0"
     }, {
       "arch" : "x86_64",
       "description" : "AI inference application development, preconfigured ModelBox, AI engine PyTorch, TensorRT and TensorFlow, only SSH connection supported.",
       "dev_services" : [ "AI_FLOW", "SSH" ],
       "id" : "e1a07296-22a8-4f05-8bc8-e936c8e54101",
       "name" : "modelbox1.1.1.5-tensorrt7.1.3-pytorch1.9.1-cuda10.2-cudnn8-euler2.9.6",
       "resource_categories" : [ "GPU" ],
       "status" : "ACTIVE",
       "swr_path" : ".xxxx.com/atelier/modelarts-aiflow-gpu-x86:1.1.2.1",
       "tag" : "1.1.2.1",
       "type" : "BUILD_IN",
       "update_at" : 1636451722844,
       "workspace_id" : "0"
     }, {
       "arch" : "aarch64",
       "description" : "AI inference application development, preconfigured ModelBox and AI engine MindSpore, only SSH connection supported.",
       "dev_services" : [ "AI_FLOW", "SSH" ],
       "id" : "e1a07296-22a8-4f05-8bc8-e936c8e54102",
       "name" : "modelbox-mindspore5.1.5-cann20.2-euler2.9.5-aarch64",
       "resource_categories" : [ "ASCEND" ],
       "status" : "ACTIVE",
       "swr_path" : ".xxxx.com/atelier/modelarts_aiflow_ascend_aarch64:1.0.4.1",
       "tag" : "1.0.4.1",
       "type" : "BUILD_IN",
       "update_at" : 1638425872501,
       "workspace_id" : "0"
     }, {
       "arch" : "aarch64",
       "description" : "Ascend+ARM algorithm development and training. TensorFlow and MindSpore are preset in the AI engine.",
       "dev_services" : [ "NOTEBOOK", "SSH" ],
       "id" : "e1a07296-22a8-4f05-8bc8-e936c8e54097",
       "name" : "tensorflow1.15-mindspore1.2.0-cann20.2-euler2.8-aarch64",
       "resource_categories" : [ "CPU", "ASCEND" ],
       "status" : "ACTIVE",
       "swr_path" : ".xxxx.com/atelier/notebook2.0-mul-kernel-arm-ascend-cp37:3.3.2-c79_release_v3",
       "tag" : "3.3.2-c79_release_v3",
       "type" : "BUILD_IN",
       "workspace_id" : "0"
     }, {
       "arch" : "aarch64",
       "description" : "Ascend+ARM algorithm development and training. TensorFlow and MindSpore are preset in the AI engine.",
       "dev_services" : [ "NOTEBOOK", "SSH" ],
       "id" : "59a6e9f5-93c0-44dd-85b0-82f390c5d53b",
       "name" : "tensorflow1.15-mindspore1.3.0-cann20.2-euler2.8-aarch64",
       "resource_categories" : [ "ASCEND" ],
       "status" : "ACTIVE",
       "swr_path" : ".xxxx.com/atelier/notebook2.0-mul-kernel-arm-ascend-cp37:3.3.2-c79_release_v3",
       "tag" : "3.3.2-c79_release_v3",
       "type" : "BUILD_IN",
       "update_at" : 1632470275633,
       "workspace_id" : "0"
     }, {
       "arch" : "aarch64",
       "description" : "Ascend operator development. The professional operator development tool MindStudio is preconfigured, only SSH connection supported.",
       "dev_services" : [ "SSH" ],
       "id" : "42dbf97e-5e26-4d7f-a836-193ffc3fa78e",
       "name" : "mindstudio3.0.2-ascend910-cann3.3.0-ubuntu18.04-aarch64",
       "resource_categories" : [ "ASCEND" ],
       "status" : "ACTIVE",
       "swr_path" : ".xxxx.com/atelier/mindstudio-modelarts-image:0830",
       "tag" : "0830",
       "type" : "BUILD_IN",
       "workspace_id" : "0"
     }, {
       "arch" : "x86_64",
       "description" : "pytorch_1.4-move-modelarts_develop",
       "dev_services" : [ "NOTEBOOK" ],
       "id" : "9dcaa52c-5bc8-4030-96a7-62f099ec2003",
       "name" : "pytorch_1.4-move-modelarts_develop",
       "resource_categories" : [ "CPU" ],
       "status" : "ACTIVE",
       "swr_path" : ".xxxx.com/atelier/notebook2.0-pytorch-1-4-kernel-cp37:devel-pytorch_1.4-move-modelarts_develop-v4",
       "tag" : "devel-pytorch_1.4-move-modelarts_develop-v4",
       "type" : "BUILD_IN",
       "workspace_id" : "0"
     }, {
       "arch" : "x86_64",
       "description" : "tensorflow-1.13-cuda10.0",
       "dev_services" : [ "NOTEBOOK" ],
       "id" : "34644333-e2f0-4fa3-915f-7c783ddc004d",
       "name" : "tensorflow-1.13-cuda10.0",
       "resource_categories" : [ "GPU" ],
       "status" : "ACTIVE",
       "swr_path" : ".xxxx.com/atelier/notebook2.0-tensorflow-1.13-kernel-cp37:3.3.1.release",
       "tag" : "3.3.1.release",
       "type" : "BUILD_IN",
       "workspace_id" : "0"
     }, {
       "arch" : "x86_64",
       "description" : "CPU and GPU general algorithm development and training, preconfigured with AI engine PyTorch1.8",
       "dev_services" : [ "NOTEBOOK", "SSH" ],
       "id" : "278e88d1-5b71-4766-8502-b3ba72e824d9",
       "name" : "pytorch1.8-cuda10.2-cudnn7-ubuntu18.04",
       "resource_categories" : [ "CPU", "GPU" ],
       "status" : "ACTIVE",
       "swr_path" : ".xxxx.com/atelier/notebook2.0-pytorch-1.8-kernel-cp37:3.3.3-B003-20211220",
       "tag" : "3.3.3-B003-20211220",
       "type" : "BUILD_IN",
       "update_at" : 1638234504492,
       "workspace_id" : "0"
     }, {
       "arch" : "x86_64",
       "description" : "MXNet-1.2.1, PySpark-2.3.2, Pytorch-1.0.0, TensorFlow-1.13.1, TensorFlow-1.8, XGBoost-Sklearn",
       "dev_services" : [ ],
       "id" : "e1a07296-22a8-4f05-8bc8-e936c8e54091",
       "name" : "notebook2.0-mul-kernel-cpu-cp36",
       "resource_categories" : [ "GPU" ],
       "status" : "ACTIVE",
       "swr_path" : ".xxxx.com/atelier/notebook2.0-mul-kernel-gpu-cp36:3.3.3-B003-20211220",
       "tag" : "3.3.3-B003-20211220",
       "type" : "BUILD_IN",
       "workspace_id" : "0"
     }, {
       "arch" : "x86_64",
       "description" : "GPU algorithm development and training, preconfigured with AI engine TensorFlow1.13.1",
       "dev_services" : [ "NOTEBOOK", "SSH" ],
       "id" : "b80bbf3d-a7af-42f6-ad12-33ff9116ab0d",
       "name" : "tensorflow1.13-cuda10.0-cudnn7-ubuntu18.04",
       "resource_categories" : [ "GPU" ],
       "status" : "ACTIVE",
       "swr_path" : ".xxxx.com/atelier/notebook2.0-tensorflow-1.13-kernel-cp37:3.3.3-B003-20211220",
       "tag" : "3.3.3-B003-20211220",
       "type" : "BUILD_IN",
       "update_at" : 1638234923985,
       "workspace_id" : "0"
     }, {
       "arch" : "x86_64",
       "description" : "user_define_base",
       "dev_services" : [ "NOTEBOOK", "SSH" ],
       "id" : "e2f03e58-b743-41fb-bd18-00ba814fbe82",
       "name" : "user_define_base",
       "resource_categories" : [ "CPU" ],
       "status" : "ACTIVE",
       "swr_path" : ".xxxx.com/atelier/user_defined_base:ubuntu_18.04-x86_64-20211028190608-439572b",
       "tag" : "ubuntu_18.04-x86_64-20211028190608-439572b",
       "type" : "BUILD_IN",
       "workspace_id" : "0"
     }, {
       "arch" : "x86_64",
       "description" : "user_define_base_cuda10.2",
       "dev_services" : [ "NOTEBOOK", "SSH" ],
       "id" : "ee8e6602-5462-43ec-ac84-a08a78e41cfb",
       "name" : "user_define_base_cuda10.2",
       "resource_categories" : [ "GPU" ],
       "status" : "ACTIVE",
       "swr_path" : ".xxxx.com/atelier/user_defined_base:cuda_10.2-ubuntu_18.04-x86_64-20211028190608-439572b",
       "tag" : "cuda_10.2-ubuntu_18.04-x86_64-20211028190608-439572b",
       "type" : "BUILD_IN",
       "workspace_id" : "0"
     }, {
       "arch" : "x86_64",
       "description" : "MXNet-1.2.1, PySpark-2.3.2, Pytorch-1.0.0, TensorFlow-1.13.1, TensorFlow-1.8, XGBoost-Sklearn",
       "dev_services" : [ "NOTEBOOK", "SSH" ],
       "id" : "e1a07296-22a8-4f05-8bc8-e936c8e54090",
       "name" : "notebook2.0-mul-kernel-cpu-cp36",
       "resource_categories" : [ "CPU" ],
       "status" : "ACTIVE",
       "swr_path" : ".xxxx.com/atelier/notebook2.0-mul-kernel-cpu-cp36:3.3.3-B003-20211220",
       "tag" : "3.3.3-B003-20211220",
       "type" : "BUILD_IN",
       "update_at" : 1604442650857,
       "workspace_id" : "0"
     }, {
       "arch" : "x86_64",
       "create_at" : 1615264782906,
       "description" : "CPU operations research development, preconfigured with cylp, cbcpy, ortools, cplex(community).",
       "dev_services" : [ "NOTEBOOK", "SSH" ],
       "id" : "daf39542-ebe5-4073-a3a4-353efd519691",
       "name" : "cylp0.91.4-cbcpy2.10-ortools9.0-cplex20.1.0-ubuntu18.04",
       "namespace" : "rl-dev",
       "resource_categories" : [ "CPU" ],
       "status" : "ACTIVE",
       "swr_path" : ".xxxx.com/rl-dev/or-cpu:1.0.8",
       "tag" : "1.0.8",
       "type" : "BUILD_IN",
       "update_at" : 1615404250789,
       "workspace_id" : "0"
     }, {
       "arch" : "x86_64",
       "description" : "CPU and GPU algorithm development and training, preconfigured with AI engine ray for reinforcement learning.",
       "dev_services" : [ "NOTEBOOK" ],
       "id" : "706e03fb-650b-44da-a3ba-6191ba7e62c7",
       "name" : "rlstudio1.0.0-ray1.3.0-cuda10.1-ubuntu18.04 ",
       "resource_categories" : [ "CPU", "GPU" ],
       "status" : "ACTIVE",
       "swr_path" : ".xxxx.com/atelier/notebook2.0-rl-1.0.0-kernel-cp37:rl-v220211130",
       "tag" : "rl-v220211130",
       "type" : "BUILD_IN",
       "workspace_id" : "0"
     }, {
       "arch" : "x86_64",
       "dev_services" : [ "NOTEBOOK" ],
       "id" : "1d1b1327-b243-425b-ad81-2689584c1acc",
       "name" : "mls-feature-engineering",
       "resource_categories" : [ "CPU" ],
       "status" : "ACTIVE",
       "swr_path" : ".xxxx.com/atelier/notebook2.0-mul-kernel-mls-feature-engineering-cpu-py37:3.2.01090103",
       "tag" : "3.2.01090103",
       "type" : "BUILD_IN",
       "workspace_id" : "0"
     }, {
       "arch" : "x86_64",
       "dev_services" : [ ],
       "id" : "88bd7bcd-0c91-45b2-ad0e-ef65553d19c5",
       "name" : "dls-feature-engineering",
       "resource_categories" : [ "CPU" ],
       "status" : "ACTIVE",
       "swr_path" : ".xxxx.com/atelier/notebook2.0-mul-kernel-dls-feature-engineering-cpu-py37:2.0.109",
       "tag" : "2.0.109",
       "type" : "BUILD_IN",
       "workspace_id" : "0"
     } ],
     "pages" : 1,
     "size" : 200,
     "total" : 28
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
