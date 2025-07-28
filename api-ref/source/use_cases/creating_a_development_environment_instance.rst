:original_name: modelarts_03_0406.html

.. _modelarts_03_0406:

Creating a Development Environment Instance
===========================================

This section describes how to create a development environment instance by calling ModelArts APIs.

Overview
--------

The process for creating a development environment instance is as follows:

#. Call the API for :ref:`authentication <modelarts_03_0004>` to obtain a user token, which will be added in a request header for authentication.
#. Call the API for :ref:`querying supported images <listimage>` to view the image type and version in the development environment.
#. Call the API for :ref:`creating a notebook instance <createnotebook>` to create an instance.
#. Call the API for :ref:`querying details of a notebook instance <shownotebook>` to query the instance creation details based on the instance ID.
#. Call the API for :ref:`prolonging a notebook instance <renewlease>` to reset the usage duration of the instance.
#. Call the API for :ref:`stopping a notebook instance <stopnotebook>` to stop the instance that is running.
#. Call the API for :ref:`starting a notebook instance <startnotebook>` to restart the instance.
#. Call the API for :ref:`deleting a notebook instance <deletenotebook>` to delete the instance that is no longer needed.

Prerequisites
-------------

-  You have obtained the endpoints of :ref:`ModelArts <modelarts_03_0141>`.
-  The following information is available: region where ModelArts is deployed, :ref:`project ID and name <modelarts_03_0147>`, :ref:`account name and ID <modelarts_03_0148>`, and :ref:`username and user ID <modelarts_03_0006>`.

Procedure
---------

#. Call the API for :ref:`querying supported images <listimage>` to view the image type and version in the development environment.

   a. Request body:

      URI: GET https://*{ma_endpoint}*/v1/*{project_id}*/images

      Request header:

      -  X-auth-Token →\ **MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...**
      -  Content-Type →application/json

      Set the following parameters based on site requirements:

      -  *ma_endpoint*: ModelArts endpoint
      -  *project_id*: user's project ID
      -  **X-auth-Token**: token obtained in the previous step

   b. Status code **200** is returned. The response body is as follows:

      .. code-block::

         {
          "current": 0,
          "data": [
           {
            "arch": "x86_64",
            "description": "CPU and GPU general algorithm development and training, preconfigured with AI engine PyTorch1.8",
            "dev_services": [
             "NOTEBOOK",
             "SSH"
            ],
            "id": "278e88d1-5b71-4766-8502-b3ba72e824d9",
            "name": "pytorch1.8-cuda10.2-cudnn7-ubuntu18.04",
            "resource_categories": [
             "CPU",
             "GPU"
            ],
            "service_type": "COMMON",
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/pytorch_1_8:pytorch_1.8.0-cuda_10.2-py_3.7-ubuntu_18.04-x86_64-20221118143845-d65d817",
            "tag": "pytorch_1.8.0-cuda_10.2-py_3.7-ubuntu_18.04-x86_64-20221118143845-d65d817",
            "tags": [],
            "type": "BUILD_IN",
            "update_at": 1648866992843,
            "workspace_id": "0"
           },
           {
            "arch": "x86_64",
            "description": "CPU and GPU general algorithm development and training, preconfigured with AI engine MindSpore1.7.0 and cuda10.1",
            "dev_services": [
             "NOTEBOOK",
             "SSH"
            ],
            "id": "e1a07296-22a8-4f05-8bc8-e936c8e54202",
            "name": "mindspore1.7.0-cuda10.1-py3.7-ubuntu18.04",
            "resource_categories": [
             "GPU"
            ],
            "service_type": "TRAIN",
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/mindspore_1_7_0:mindspore_1.7.0-cuda_10.1-py_3.7-ubuntu_18.04-x86_64-20221118143809-d65d817",
            "tag": "mindspore_1.7.0-cuda_10.1-py_3.7-ubuntu_18.04-x86_64-20221118143809-d65d817",
            "tags": [],
            "type": "BUILD_IN",
            "workspace_id": "0"
           },
           {
            "arch": "x86_64",
            "description": "CPU general algorithm development and training, preconfigured with AI engine MindSpore1.7.0",
            "dev_services": [
             "NOTEBOOK",
             "SSH"
            ],
            "id": "c0b31f09-1490-4555-9b8b-ab0b2de35b20",
            "name": "mindspore1.7.0-py3.7-ubuntu18.04",
            "resource_categories": [
             "CPU"
            ],
            "service_type": "TRAIN",
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/mindspore_1_7_0:mindspore_1.7.0-cpu-py_3.7-ubuntu_18.04-x86_64-20221118143809-d65d817",
            "tag": "mindspore_1.7.0-cpu-py_3.7-ubuntu_18.04-x86_64-20221118143809-d65d817",
            "tags": [],
            "type": "BUILD_IN",
            "workspace_id": "0"
           },
           {
            "arch": "x86_64",
            "description": "CPU and GPU general algorithm development and training, preconfigured with AI engine TensorFlow2.1",
            "dev_services": [
             "NOTEBOOK",
             "SSH"
            ],
            "id": "e1a07296-22a8-4f05-8bc8-e936c8e54100",
            "name": "tensorflow2.1-cuda10.1-cudnn7-ubuntu18.04",
            "resource_categories": [
             "CPU",
             "GPU"
            ],
            "service_type": "COMMON",
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/tensorflow_2_1:tensorflow_2.1.0-cuda_10.1-py_3.7-ubuntu_18.04-x86_64-20221121111529-d65d817",
            "tag": "tensorflow_2.1.0-cuda_10.1-py_3.7-ubuntu_18.04-x86_64-20221121111529-d65d817",
            "tags": [],
            "type": "BUILD_IN",
            "update_at": 1643166780367,
            "workspace_id": "0"
           },
           {
            "arch": "x86_64",
            "description": "CPU and GPU general algorithm development and training, preconfigured with AI engine PyTorch1.10 and cuda10.2",
            "dev_services": [
             "NOTEBOOK",
             "SSH"
            ],
            "id": "d996b661-e127-48c4-a90a-fca29535f201",
            "name": "pytorch1.10-cuda10.2-cudnn7-ubuntu18.04",
            "resource_categories": [
             "CPU",
             "GPU"
            ],
            "service_type": "UNKNOWN",
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/pytorch_1_10:pytorch_1.10.2-cuda_10.2-py_3.7-ubuntu_18.04-x86_64-20221118143845-d65d817",
            "tag": "pytorch_1.10.2-cuda_10.2-py_3.7-ubuntu_18.04-x86_64-20221118143845-d65d817",
            "tags": [],
            "type": "BUILD_IN",
            "workspace_id": "0"
           },
           {
            "arch": "x86_64",
            "description": "Clean user customized base image include cuda10.2, conda",
            "dev_services": [
             "NOTEBOOK",
             "SSH"
            ],
            "id": "d937149a-785c-4d2d-a568-8dde7c06cca0",
            "name": "conda3-cuda10.2-cudnn7-ubuntu18.04",
            "resource_categories": [
             "GPU"
            ],
            "service_type": "UNKNOWN",
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/user_defined_base:cuda_10.2-ubuntu_18.04-x86_64-20230404095316-7fcd503",
            "tag": "cuda_10.2-ubuntu_18.04-x86_64-20230404095316-7fcd503",
            "tags": [],
            "type": "BUILD_IN",
            "workspace_id": "0"
           },
           {
            "arch": "x86_64",
            "description": "Clean user customized base image only include conda",
            "dev_services": [
             "NOTEBOOK",
             "SSH"
            ],
            "id": "27542a4a-3b37-404d-add9-a7d2d2ce6893",
            "name": "conda3-ubuntu18.04",
            "resource_categories": [
             "CPU"
            ],
            "service_type": "UNKNOWN",
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/user_defined_base:ubuntu_18.04-x86_64-20230404095316-7fcd503",
            "tag": "ubuntu_18.04-x86_64-20230404095316-7fcd503",
            "tags": [],
            "type": "BUILD_IN",
            "workspace_id": "0"
           },
           {
            "arch": "x86_64",
            "description": "CPU and GPU general algorithm development and training, preconfigured with AI engine PyTorch1.4",
            "dev_services": [
             "NOTEBOOK",
             "SSH"
            ],
            "id": "e1a07296-22a8-4f05-8bc8-e936c8e54099",
            "name": "pytorch1.4-cuda10.1-cudnn7-ubuntu18.04",
            "resource_categories": [
             "CPU",
             "GPU"
            ],
            "service_type": "TRAIN",
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/pytorch_1_4:pytorch_1.4-cuda_10.1-py37-ubuntu_18.04-x86_64-20221118143845-d65d817",
            "tag": "pytorch_1.4-cuda_10.1-py37-ubuntu_18.04-x86_64-20221118143845-d65d817",
            "tags": [],
            "type": "BUILD_IN",
            "update_at": 1648866992868,
            "workspace_id": "0"
           },
           {
            "arch": "x86_64",
            "description": "GPU algorithm development and training, preconfigured with AI engine TensorFlow1.13.1",
            "dev_services": [
             "NOTEBOOK",
             "SSH"
            ],
            "id": "b80bbf3d-a7af-42f6-ad12-33ff9116ab0d",
            "name": "tensorflow1.13-cuda10.0-cudnn7-ubuntu18.04",
            "resource_categories": [
             "GPU"
            ],
            "service_type": "TRAIN",
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/tensorflow_1_13:tensorflow_1.13-cuda_10.0-py_3.7-ubuntu_18.04-x86_64-20221118143845-d65d817",
            "tag": "tensorflow_1.13-cuda_10.0-py_3.7-ubuntu_18.04-x86_64-20221118143845-d65d817",
            "tags": [],
            "type": "BUILD_IN",
            "update_at": 1648866992960,
            "workspace_id": "0"
           },
           {
            "arch": "aarch64",
            "create_at": 1608937196685,
            "description": "Ascend+ARM algorithm development and training. TensorFlow and MindSpore are preset in the AI engine.",
            "dev_services": [
             "NOTEBOOK",
             "SSH"
            ],
            "id": "59a6e9f5-93c0-44dd-85b0-82f390c5d53a",
            "name": "tensorflow1.15-mindspore1.7.0-cann5.1.0-euler2.8-aarch64",
            "resource_categories": [
             "ASCEND"
            ],
            "service_type": "TRAIN",
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/notebook2.0-mul-kernel-arm-ascend-cp37:5.0.1-c81-20220726",
            "tag": "5.0.1-c81-20220726",
            "tags": [],
            "type": "BUILD_IN",
            "update_at": 1648866992983,
            "workspace_id": "0"
           },
           {
            "arch": "x86_64",
            "description": "AI inference application development, preconfigured ModelBox and AI engine LibTorch, only SSH connection supported.",
            "dev_services": [
             "AI_FLOW",
             "SSH"
            ],
            "id": "e1a07296-22a8-4f05-8bc8-e936c8e54103",
            "name": "modelbox1.3.0-libtorch1.9.1-cuda10.2-cudnn8-euler2.9.6",
            "resource_categories": [
             "GPU"
            ],
            "service_type": "TRAIN",
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/modelarts-modelbox-libtorch-gpu-x86:1.3.0-20221223142251-b3da6d6",
            "tag": "1.3.0-20221223142251-b3da6d6",
            "tags": [],
            "type": "BUILD_IN",
            "update_at": 1648866993005,
            "workspace_id": "0"
           },
           {
            "arch": "x86_64",
            "description": "AI inference application development, preconfigured ModelBox and AI engine TensorRT, only SSH connection supported.",
            "dev_services": [
             "AI_FLOW",
             "SSH"
            ],
            "id": "e1a07296-22a8-4f05-8bc8-e936c8e54101",
            "name": "modelbox1.3.0-tensorrt7.1.3-cuda10.2-cudnn8-euler2.9.6",
            "resource_categories": [
             "GPU"
            ],
            "service_type": "TRAIN",
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/modelarts-modelbox-tensorrt-gpu-x86:1.3.0-20221223142251-b3da6d6",
            "tag": "1.3.0-20221223142251-b3da6d6",
            "tags": [],
            "type": "BUILD_IN",
            "update_at": 1648866993030,
            "workspace_id": "0"
           },
           {
            "arch": "aarch64",
            "description": "Ascend operator development. The professional operator development tool MindStudio is preconfigured, only SSH connection supported.",
            "dev_services": [
             "SSH"
            ],
            "id": "e1a07296-22a8-4f05-8bc8-e936c8e54088",
            "name": "mindstudio5.0.rc1-ascendsnt9-cann5.1.0-euler2.8.3-aarch64",
            "resource_categories": [
             "ASCEND"
            ],
            "service_type": "TRAIN",
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/mindstudio-modelarts-image:5.0.rc1-20230322101430-75f458a",
            "tag": "5.0.rc1-20230322101430-75f458a",
            "tags": [],
            "type": "BUILD_IN",
            "update_at": 1648866993052,
            "workspace_id": "0"
           },
           {
            "arch": "x86_64",
            "description": "CPU algorithm development and training, preconfigured PySpark 2.4.5 and scala 2.11.12 for code development in local notebook and remote spark cluster including MRS and DLI",
            "dev_services": [
             "NOTEBOOK"
            ],
            "id": "0b2d0728-4c01-11ec-994f-001a7dda7112",
            "name": "spark2.4.5-ubuntu18.04",
            "resource_categories": [
             "CPU"
            ],
            "service_type": "TRAIN",
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/pyspark_2_4_5:develop-remote-pyspark_2.4.5-py_3.7-cpu-ubuntu_18.04-x86_64-uid1000-20221222203856-fcc979e",
            "tag": "develop-remote-pyspark_2.4.5-py_3.7-cpu-ubuntu_18.04-x86_64-uid1000-20221222203856-fcc979e",
            "tags": [],
            "type": "BUILD_IN",
            "update_at": 1648867218663,
            "workspace_id": "0"
           },
           {
            "arch": "x86_64",
            "create_at": 1605759392357,
            "description": "CPU algorithm development and training, preconfigured with the AI engine MindSpore-CPU",
            "dev_services": [
             "NOTEBOOK",
             "SSH"
            ],
            "id": "65f636a0-56cf-49df-b941-7d2a07ba8c8c",
            "name": "mindspore1.2.0-openmpi2.1.1-ubuntu18.04",
            "resource_categories": [
             "CPU"
            ],
            "service_type": "TRAIN",
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/mindspore_1_2_0:mindspore_1.2.0-py_3.7-ubuntu_18.04-x86_64-20221118143809-d65d817",
            "tag": "mindspore_1.2.0-py_3.7-ubuntu_18.04-x86_64-20221118143809-d65d817",
            "tags": [],
            "type": "BUILD_IN",
            "update_at": 1643166780389,
            "workspace_id": "0"
           },
           {
            "arch": "x86_64",
            "create_at": 1664501979865,
            "description": "",
            "dev_services": [
             "NOTEBOOK",
             "SSH"
            ],
            "id": "df78b3f7-98a4-4616-aef0-71cfff4195c9",
            "name": "spark",
            "namespace": "testdli002",
            "origin": "CUSTOMIZE",
            "resource_categories": [
             "CPU"
            ],
            "service_type": "UNKNOWN",
            "size": 1133670676,
            "status": "ACTIVE",
            "swr_path": "swr.com/testdli002/spark:2.4.5.tensorflow",
            "tag": "2.4.5.tensorflow",
            "tags": [],
            "type": "DEDICATED",
            "update_at": 1664501979865,
            "visibility": "PRIVATE",
            "workspace_id": "0"
           },
           {
            "arch": "x86_64",
            "create_at": 1664513619044,
            "description": "",
            "dev_services": [
             "NOTEBOOK",
             "SSH"
            ],
            "id": "836ab55d-4a02-4dbb-b04f-ece555d642a8",
            "name": "tensorflow2_1_1",
            "namespace": "hwstaff_pub_cbuinfo_ei",
            "origin": "IMAGE_SAVE",
            "resource_categories": [
             "CPU",
             "GPU"
            ],
            "service_type": "COMMON",
            "size": 5094544544,
            "status": "ERROR",
            "status_message": "",
            "swr_path": "swr.com/hwstaff_pub_cbuinfo_ei/tensorflow2_1_1:1.0.0",
            "tag": "1.0.0",
            "tags": [],
            "type": "DEDICATED",
            "update_at": 1664513676950,
            "visibility": "PRIVATE",
            "workspace_id": "0"
           },
           {
            "arch": "x86_64",
            "create_at": 1668482562290,
            "description": "test",
            "dev_services": [
             "NOTEBOOK",
             "SSH"
            ],
            "id": "689c81b3-15dd-4500-b63e-1871e24eb391",
            "name": "pytorch_1_8",
            "namespace": "atelier",
            "origin": "CUSTOMIZE",
            "resource_categories": [
             "GPU"
            ],
            "service_type": "UNKNOWN",
            "size": 8285974481,
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/pytorch_1_8:pytorch_1.8.2-cuda_11.1-py_3.7-ubuntu_18.04-x86_64-20220926104358-041ba2e",
            "tag": "pytorch_1.8.2-cuda_11.1-py_3.7-ubuntu_18.04-x86_64-20220926104358-041ba2e",
            "tags": [],
            "type": "DEDICATED",
            "update_at": 1668482562290,
            "visibility": "PRIVATE",
            "workspace_id": "0"
           },
           {
            "arch": "aarch64",
            "description": "Ascend+ARM algorithm development and training. MindSpore is preset in the AI engine.",
            "dev_services": [
             "NOTEBOOK",
             "SSH"
            ],
            "id": "f6d0908e-9596-41f9-9843-83089cbdd0de",
            "name": "mindspore1.7.0-cann5.1.0-py3.7-euler2.8.3",
            "namespace": "atelier",
            "resource_categories": [
             "ASCEND"
            ],
            "service_type": "UNKNOWN",
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/mindspore_1_7_0:mindspore_1.7.0-cann_5.1.0-py_3.7-euler_2.8.3-aarch64-snt9-20220906",
            "tag": "mindspore_1.7.0-cann_5.1.0-py_3.7-euler_2.8.3-aarch64-snt9-20220906",
            "tags": [],
            "type": "BUILD_IN",
            "workspace_id": "0"
           },
           {
            "arch": "aarch64",
            "description": "Ascend+ARM algorithm development and training. TensorFlow is preset in the AI engine.",
            "dev_services": [
             "NOTEBOOK",
             "SSH"
            ],
            "id": "c5b7507b-ca8d-48d5-a373-fe4b42c66ed8",
            "name": "tensorflow1.15-cann5.1.0-py3.7-euler2.8.3",
            "namespace": "atelier",
            "resource_categories": [
             "ASCEND"
            ],
            "service_type": "UNKNOWN",
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/tensorflow_1_15_ascend:tensorflow_1.15-cann_5.1.0-py_3.7-euler_2.8.3-aarch64-snt9-20220906",
            "tag": "tensorflow_1.15-cann_5.1.0-py_3.7-euler_2.8.3-aarch64-snt9-20220906",
            "tags": [],
            "type": "BUILD_IN",
            "workspace_id": "0"
           },
           {
            "arch": "x86_64",
            "create_at": 1678261148079,
            "description": "",
            "dev_services": [
             "NOTEBOOK",
             "SSH"
            ],
            "id": "e1ab81ef-f452-46b5-9663-6fc1f982f9e9",
            "name": "grafana",
            "namespace": "hwstaff_pub_cbuinfo_ei",
            "origin": "IMAGE_SAVE",
            "resource_categories": [
             "CPU",
             "GPU"
            ],
            "service_type": "COMMON",
            "size": 5247805223,
            "status": "ACTIVE",
            "status_message": "",
            "swr_path": "swr.com/hwstaff_pub_cbuinfo_ei/grafana:v1.0",
            "tag": "v1.0",
            "tags": [],
            "type": "DEDICATED",
            "update_at": 1678261330238,
            "visibility": "PRIVATE",
            "workspace_id": "0"
           },
           {
            "arch": "x86_64",
            "create_at": 1681973786157,
            "dev_services": [
             "NOTEBOOK",
             "SSH"
            ],
            "id": "a5a43175-30a6-43d2-9596-38bee562f8c0",
            "name": "pytorch_1_8",
            "namespace": "sdk-test2",
            "origin": "CUSTOMIZE",
            "resource_categories": [
             "CPU",
             "GPU"
            ],
            "service_type": "UNKNOWN",
            "size": 2308736380,
            "status": "ACTIVE",
            "swr_path": "swr.com/sdk-test2/pytorch_1_8:v2",
            "tag": "v2",
            "tags": [],
            "type": "DEDICATED",
            "update_at": 1681973786157,
            "visibility": "PRIVATE",
            "workspace_id": "0"
           },
           {
            "arch": "aarch64",
            "create_at": 1682670088194,
            "description": "Ascend+ARM algorithm development and training. MindSpore is preset in the AI engine.",
            "dev_services": [
             "NOTEBOOK",
             "SSH"
            ],
            "id": "75cbf0f2-0a3e-48c9-b2c4-7e78af18d86e",
            "name": "mindspore_1.9.0-cann_6.0.0-py_3.7-euler_2.8.3",
            "namespace": "atelier",
            "resource_categories": [
             "ASCEND"
            ],
            "service_type": "TRAIN",
            "size": 4011027643,
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/mindspore_1_9_ascend:mindspore_1.9.0-cann_6.0.0-py_3.7-euler_2.8.3-aarch64-snt9-20221116111529",
            "tag": "mindspore_1.9.0-cann_6.0.0-py_3.7-euler_2.8.3-aarch64-snt9-20221116111529",
            "tags": [],
            "type": "BUILD_IN",
            "update_at": 1682670088197,
            "visibility": "PUBLIC",
            "workspace_id": "0"
           },
           {
            "arch": "x86_64",
            "description": "notebook2.0 gpu",
            "dev_services": [
             "NOTEBOOK",
             "SSH"
            ],
            "id": "e1a07296-22a8-4f05-8bc8-e936c8e54092",
            "name": "notebook2.0-mul-kernel-cpu-cp36",
            "resource_categories": [
             "GPU"
            ],
            "service_type": "TRAIN",
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/notebook2.0-mul-kernel-gpu-cp36:5.0.1-release-v2-20220505",
            "tag": "5.0.1-release-v2-20220505",
            "tags": [],
            "type": "BUILD_IN",
            "update_at": 1628221753209,
            "workspace_id": "0"
           },
           {
            "arch": "aarch64",
            "create_at": 1683537880541,
            "description": "Ascend+ARM algorithm development and training. MindSpore is preset in the AI engine.",
            "dev_services": [
             "NOTEBOOK",
             "SSH"
            ],
            "id": "31ae7ba4-63e6-4fa6-8aeb-cb382953e414",
            "name": "mindspore_1.10.0-cann_6.0.1-py_3.7-euler_2.8.3",
            "namespace": "atelier",
            "resource_categories": [
             "ASCEND"
            ],
            "service_type": "COMMON",
            "size": 4057170552,
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/mindspore_1_10_ascend:mindspore_1.10.0-cann_6.0.1-py_3.7-euler_2.8.3-aarch64-snt9-20230303173945-815d627",
            "tag": "mindspore_1.10.0-cann_6.0.1-py_3.7-euler_2.8.3-aarch64-snt9-20230303173945-815d627",
            "tags": [],
            "type": "BUILD_IN",
            "update_at": 1683537880548,
            "visibility": "PUBLIC",
            "workspace_id": "0"
           },
           {
            "arch": "x86_64",
            "description": "CPU algorithm development and training, including the MLStudio tool for graphical ML algorithm development, and preconfigured PySpark 2.3.2",
            "dev_services": [
             "NOTEBOOK"
            ],
            "id": "0e5f9a41-c9c2-4d9a-a190-4e1b17a7782f",
            "name": "mlstudio-pyspark2.3.2-ubuntu16.04",
            "resource_categories": [
             "CPU"
            ],
            "service_type": "TRAIN",
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/notebook2.0-mlstudio-cp36:3.3.1.9",
            "tag": "3.3.1.9",
            "tags": [],
            "type": "BUILD_IN",
            "update_at": 1648867218685,
            "workspace_id": "0"
           },
           {
            "arch": "x86_64",
            "description": "notebook2.0 cpu base image",
            "dev_services": [
             "NOTEBOOK",
             "SSH"
            ],
            "id": "e1a07296-22a8-4f05-8bc8-e936c8e54090",
            "name": "notebook2.0-mul-kernel-cpu-cp36",
            "resource_categories": [
             "CPU"
            ],
            "service_type": "TRAIN",
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/notebook2.0-mul-kernel-cpu-cp36:5.0.1-release-v2-20220505",
            "tag": "5.0.1-release-v2-20220505",
            "tags": [],
            "type": "BUILD_IN",
            "update_at": 1628221753345,
            "workspace_id": "0"
           },
           {
            "arch": "x86_64",
            "description": "GPU algorithm development and training, preconfigured with the AI engine MindSpore-GPU",
            "dev_services": [
             "NOTEBOOK",
             "SSH"
            ],
            "id": "d7fb5355-9045-4deb-94c6-4033e1e62728",
            "name": "mindspore1.2.0-openmpi2.1.1-ubuntu18.04",
            "resource_categories": [
             "GPU"
            ],
            "service_type": "TRAIN",
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/mindspore_1_2_0:mindspore_1.2.0-py_3.7-ubuntu_18.04-x86_64-20221118143809-d65d817",
            "tag": "mindspore_1.2.0-py_3.7-ubuntu_18.04-x86_64-20221118143809-d65d817",
            "tags": [],
            "type": "BUILD_IN",
            "update_at": 1636963735672,
            "workspace_id": "0"
           },
           {
            "arch": "x86_64",
            "create_at": 1628757809703,
            "description": "CPU operations research development, preconfigured with cylp, cbcpy, ortools, cplex(community).",
            "dev_services": [
             "NOTEBOOK",
             "SSH"
            ],
            "id": "b9933af0-3119-4045-a427-5e668327dafd",
            "name": "cylp0.91.4-cbcpy2.10-ortools9.0-cplex20.1.0-ubuntu18.04",
            "namespace": "atelier",
            "resource_categories": [
             "CPU"
            ],
            "service_type": "TRAIN",
            "size": 2550402546,
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/or_1_0_0:or_1.0.0-py_3.7-ubuntu_18.04-x86_64-roma-20220812093355-e50493d",
            "tag": "or_1.0.0-py_3.7-ubuntu_18.04-x86_64-roma-20220812093355-e50493d",
            "tags": [],
            "type": "BUILD_IN",
            "update_at": 1642836699554,
            "workspace_id": "0"
           },
           {
            "arch": "x86_64",
            "description": "CPU algorithm development and training, including the MLStudio tool for graphical ML algorithm development, and preconfigured PySpark 2.4.5",
            "dev_services": [
             "NOTEBOOK"
            ],
            "id": "0b2d0728-4c01-11ec-994f-001a7dda7111",
            "name": "mlstudio-pyspark2.4.5-ubuntu18.04",
            "resource_categories": [
             "CPU"
            ],
            "service_type": "TRAIN",
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/notebook2.0-mlstudio-cp37:5.0.1-mls-20230118153946",
            "tag": "5.0.1-mls-20230118153946",
            "tags": [],
            "type": "BUILD_IN",
            "update_at": 1648867218708,
            "workspace_id": "0"
           },
           {
            "arch": "x86_64",
            "create_at": 1605759392404,
            "description": "GPU algorithm development and training, preconfigured with the AI engine MindSpore-GPU",
            "dev_services": [
             "NOTEBOOK",
             "SSH"
            ],
            "id": "89de30ec-6871-4f22-84af-be37ef28335d",
            "name": "mindspore1.2.0-cuda10.1-cudnn7-ubuntu18.04",
            "resource_categories": [
             "GPU"
            ],
            "service_type": "TRAIN",
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/mindspore_1_2_0:mindspore_1.2.0-py_3.7-cuda_10.1-ubuntu_18.04-x86_64-20221118143809-d65d817",
            "tag": "mindspore_1.2.0-py_3.7-cuda_10.1-ubuntu_18.04-x86_64-20221118143809-d65d817",
            "tags": [],
            "type": "BUILD_IN",
            "update_at": 1648867218639,
            "workspace_id": "0"
           },
           {
            "arch": "x86_64",
            "description": "description",
            "dev_services": [
             "NOTEBOOK"
            ],
            "id": "88bd7bcd-0c91-45b2-ad0e-ef65553d19c5",
            "name": "dls-feature-engineering",
            "resource_categories": [
             "CPU"
            ],
            "service_type": "TRAIN",
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/notebook2.0-mul-kernel-dls-feature-engineering-cpu-py37:3.2.0109",
            "tag": "3.2.0109",
            "tags": [],
            "type": "BUILD_IN",
            "update_at": 1623899358020,
            "workspace_id": "0"
           },
           {
            "arch": "x86_64",
            "description": "description",
            "dev_services": [
             "NOTEBOOK"
            ],
            "id": "1d1b1327-b243-425b-ad81-2689584c1acc",
            "name": "mls-feature-engineering",
            "resource_categories": [
             "CPU"
            ],
            "service_type": "TRAIN",
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/notebook2.0-mul-kernel-mls-feature-engineering-cpu-py37:3.2.0109",
            "tag": "3.2.0109",
            "tags": [],
            "type": "BUILD_IN",
            "update_at": 1623899357995,
            "workspace_id": "0"
           },
           {
            "arch": "x86_64",
            "description": "MindSpore1.7.0 and MindQuantum0.6.0",
            "dev_services": [
             "NOTEBOOK",
             "SSH"
            ],
            "id": "6592fa02-a40a-4054-a05f-f22215e45ec1",
            "name": "mindquantum0.6.0-mindspore1.7.0-ubuntu18.04",
            "resource_categories": [
             "CPU"
            ],
            "service_type": "TRAIN",
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/mindspore_1_7_0:mindspore_1.7.0-cpu-py_3.7-ubuntu_18.04-x86_64-20220727174747-6a4cdd5",
            "tag": "mindspore_1.7.0-cpu-py_3.7-ubuntu_18.04-x86_64-20220727174747-6a4cdd5",
            "tags": [],
            "type": "BUILD_IN",
            "workspace_id": "0"
           },
           {
            "arch": "x86_64",
            "create_at": 1628757853111,
            "description": "CPU and GPU algorithm development and training, preconfigured with AI engine ray for reinforcement learning.",
            "dev_services": [
             "NOTEBOOK",
             "SSH"
            ],
            "id": "4233d6f9-c3b5-4cf2-9ee6-2ef565935d6d",
            "name": "rlstudio1.0.0-ray1.3.0-cuda10.1-ubuntu18.04",
            "namespace": "rl-dev",
            "resource_categories": [
             "CPU",
             "GPU"
            ],
            "service_type": "TRAIN",
            "size": 4857883146,
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/notebook2.0-rl-1.0.0-kernel-cp37:rl-v1220211203",
            "tag": "rl-v1220211203",
            "tags": [],
            "type": "BUILD_IN",
            "update_at": 1642836699527,
            "workspace_id": "0"
           },
           {
            "arch": "aarch64",
            "description": "Ascend+ARM algorithm development and training. TensorFlow and MindSpore are preset in the AI engine.",
            "dev_services": [
             "NOTEBOOK",
             "SSH"
            ],
            "id": "59a6e9f5-93c0-44dd-85b0-82f390c5d53b",
            "name": "tensorflow1.15-mindspore1.7.0-cann5.1.0-euler2.8-aarch64",
            "resource_categories": [
             "CPU",
             "ASCEND"
            ],
            "service_type": "TRAIN",
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/notebook2.0-mul-kernel-arm-ascend-cp37:5.0.1-c81-20220726",
            "tag": "5.0.1-c81-20220726",
            "tags": [],
            "type": "BUILD_IN",
            "update_at": 1640398185602,
            "workspace_id": "0"
           },
           {
            "arch": "x86_64",
            "description": "CPU general algorithm development and training, preconfigured with AI engine MindSpore1.7.0",
            "dev_services": [
             "NOTEBOOK",
             "SSH"
            ],
            "id": "9d63f4d1-dc09-4873-b669-3483cea777c0",
            "name": "mindspore1.7.0-ubuntu18.04-default",
            "resource_categories": [
             "CPU"
            ],
            "service_type": "TRAIN",
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/mindspore_1_7_0:mindspore_1.7.0-cpu-py_3.7-ubuntu_18.04-x86_64-20220625205423-5a13f29",
            "tag": "mindspore_1.7.0-cpu-py_3.7-ubuntu_18.04-x86_64-20220625205423-5a13f29",
            "tags": [],
            "type": "BUILD_IN",
            "workspace_id": "0"
           },
           {
            "arch": "x86_64",
            "description": "CPU and GPU general algorithm development and training, preconfigured with AI engine MindSpore1.7.0 and cuda10.1",
            "dev_services": [
             "NOTEBOOK",
             "SSH"
            ],
            "id": "e1a07296-22a8-4f05-8bc8-e936c8e54203",
            "name": "mindspore1.7.0-ubuntu18.04-default",
            "resource_categories": [
             "GPU"
            ],
            "service_type": "TRAIN",
            "status": "ACTIVE",
            "swr_path": "swr.com/atelier/mindspore_1_7_0:mindspore_1.7.0-cuda_10.1-py_3.7-ubuntu_18.04-x86_64-20220625205423-5a13f29",
            "tag": "mindspore_1.7.0-cuda_10.1-py_3.7-ubuntu_18.04-x86_64-20220625205423-5a13f29",
            "tags": [],
            "type": "BUILD_IN",
            "workspace_id": "0"
           }
          ],
          "pages": 1,
          "size": 200,
          "total": 39
         }

      Select the image required for creating a notebook instance based on the **description** and **name** parameters and record its ID. This section provides an example of using TensorFlow to create a notebook instance with an **id** of **e1a07296-22a8-4f05-8bc8-e936c8e54100**.

#. Call the API for :ref:`creating a notebook instance <createnotebook>` to create an instance.

   a. Request body:

      URI: POST https://*{ma_endpoint}*/v1/*{project_id}*/notebooks

      Request header:

      -  X-auth-Token →\ **MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...**
      -  Content-Type →application/json

      Request body:

      .. code-block::

         {
           "name" : "notebooks_test",
           "feature" : "NOTEBOOK",
           "workspace_id" : "0",
           "description" : "api-test",
           "flavor" : "modelarts.vm.cpu.2u",
           "image_id" : "e1a07296-22a8-4f05-8bc8-e936c8e54090",
           "volume" : {
             "category" : "efs",
             "ownership" : "managed",
             "capacity" : 50
           }
         }

      Set the following parameters based on site requirements:

      -  *ma_endpoint*: ModelArts endpoint
      -  *project_id*: user's project ID
      -  **X-auth-Token**: token obtained in the previous step
      -  **flavor**: flavor of the notebook instance
      -  **image_id**: image ID of the notebook instance

   b. Status code **200** is returned. The response body is as follows:

      .. code-block::

         {
          "action_progress": [
           {
            "step": 4,
            "status": "WAITING",
            "description": "Initialize the notebook instance."
           },
           {
            "step": 3,
            "status": "WAITING",
            "description": "Configuring the network."
           },
           {
            "step": 2,
            "status": "WAITING",
            "description": "Prepare the compute resource."
           },
           {
            "step": 1,
            "status": "WAITING",
            "description": "Prepare the storage."
           }
          ],
          "create_at": 1687656452472,
          "description": "api-test",
          "endpoints": [],
          "feature": "NOTEBOOK",
          "flavor": "modelarts.vm.cpu.2u",
          "id": "936bea3e-d3df-435e-8b58-d817283284ae",
          "image": {
           "description": "",
           "id": "e1a07296-22a8-4f05-8bc8-e936c8e54090",
           "name": "notebook2.0-mul-kernel-cpu-cp36",
           "swr_path": "swr.com/atelier/notebook2.0-mul-kernel-cpu-cp36:5.0.1-release-v2-20220505",
           "tag": "5.0.1-release-v2-20220505",
           "type": "BUILD_IN"
          },
          "lease": {
           "create_at": 1687656452470,
           "duration": 3600000,
           "enable": true,
           "type": "TIMING",
           "update_at": 1687656452470
          },
          "name": "notebooks_test",
          "status": "RUNNING",
          "tags": [],
          "token": "3452e0d5-15fe-a20d-18a2-010a574aeaaf",
          "update_at": 1687656452588,
          "user_id": "99250e439b33431081xxxxxxxxxxa885",
          "workspace_id": "0",
          "billing_items": []
         }

      You can view the notebook instance details in the response. If **status** is **RUNNING**, the notebook instance is successfully created.

#. Call the API for :ref:`querying details of a notebook instance <shownotebook>` to query the instance creation details based on the instance ID.

   a. Request body:

      URI: GET https://*{ma_endpoint}*/v1/*{project_id}*/notebooks/*{id}*

      Request header: X-auth-Token →\ **MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...**

      Set the bold parameters based on site requirements.

   b. Status code **200** is returned. The response body is as follows:

      .. code-block::

         {
          "create_at": 1687656452472,
          "data_volumes": [],
          "description": "api-test",
          "endpoints": [
           {
            "service": "NOTEBOOK",
            "uri": "https://authoring-modelarts.com/936bea3e-d3df-435e-8b58-d817283284ae/lab"
           }
          ],
          "feature": "NOTEBOOK",
          "flavor": "modelarts.vm.cpu.2u",
          "id": "936bea3e-d3df-435e-8b58-d817283284ae",
          "image": {
           "description": "",
           "id": "e1a07296-22a8-4f05-8bc8-e936c8e54090",
           "name": "notebook2.0-mul-kernel-cpu-cp36",
           "swr_path": "swr.com/atelier/notebook2.0-mul-kernel-cpu-cp36:5.0.1-release-v2-20220505",
           "tag": "5.0.1-release-v2-20220505",
           "type": "BUILD_IN"
          },
          "lease": {
           "create_at": 1687656452470,
           "duration": 3627372,
           "enable": true,
           "type": "TIMING",
           "update_at": 1687656479842
          },
          "name": "notebooks_test",
          "status": "RUNNING",
          "tags": [],
          "token": "3452e0d5-15fe-a20d-18a2-010a574aeaaf",
          "update_at": 1687656479880,
          "url": "https://authoring-modelarts.com/936bea3e-d3df-435e-8b58-d817283284ae/lab",
          "user": {
           "domain": {
            "id": "878991804cdc4ba597xxxxxxxxxx9dd9",
            "name": "hwstaff_pub_CBUInfo_EI"
           },
           "id": "99250e439b33431081xxxxxxxxxxa885",
           "name": "xwx1128222"
          },
          "user_id": "99250e439b33431081xxxxxxxxxxa885",
          "volume": {
           "category": "EFS",
           "ownership": "MANAGED",
           "mount_path": "/home/ma-user/work/",
           "capacity": 50,
           "read_only": false
          },
          "workspace_id": "0",
          "billing_items": [
           "COMPUTE"
          ]
         }

#. Call the API for :ref:`prolonging a notebook instance <renewlease>` to reset the usage duration of the instance.

   a. Request body:

      URI: PATCH https://*{ma_endpoint}*/v1/*{project_id}*\ notebooks/*{id}*/lease

      Request header:

      -  X-auth-Token →\ **MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...**
      -  Content-Type →application/json

      Request body:

      .. code-block::

         {
           "duration": 3600000,
           "type": "timing"
         }

      Set the following parameters based on site requirements:

      -  **duration**: instance running duration, which is calculated based on the instance creation time. If the instance creation time plus the duration is greater than the current time, the system automatically stops the instance.
      -  **type**: auto stop type. The default value is **timing**.

   b. Status code **200** is returned, indicating that labeling is successful. The response body is as follows:

      .. code-block::

         {
          "create_at": 1687656452470,
          "duration": 4657544,
          "enable": true,
          "type": "TIMING",
          "update_at": 1687657510014
         }

#. Call the API for :ref:`stopping a notebook instance <stopnotebook>` to stop the instance that is running.

   a. Request body.

      URI: POSThttps://*{ma_endpoint}*//v1/*{project_id}*/notebooks/*{id}*/stop

      Request header: X-auth-Token →\ **MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...**

      Set the bold parameters based on site requirements.

   b. Status code **200** is returned. The response body is as follows:

      .. code-block::

         {
          "create_at": 1687656452472,
          "data_volumes": [],
          "description": "api-test",
          "endpoints": [
           {
            "service": "NOTEBOOK",
            "uri": "https://authoring-modelarts.com/936bea3e-d3df-435e-8b58-d817283284ae/lab"
           }
          ],
          "feature": "NOTEBOOK",
          "flavor": "modelarts.vm.cpu.2u",
          "id": "936bea3e-d3df-435e-8b58-d817283284ae",
          "image": {
           "description": "",
           "id": "e1a07296-22a8-4f05-8bc8-e936c8e54090",
           "name": "notebook2.0-mul-kernel-cpu-cp36",
           "swr_path": "swr.com/atelier/notebook2.0-mul-kernel-cpu-cp36:5.0.1-release-v2-20220505",
           "tag": "5.0.1-release-v2-20220505",
           "type": "BUILD_IN"
          },
          "lease": {
           "create_at": 1687656452470,
           "duration": 6199814,
           "enable": true,
           "type": "TIMING",
           "update_at": 1687659052284
          },
          "name": "notebooks_test",
          "status": "STOPPING",
          "tags": [],
          "token": "3452e0d5-15fe-a20d-18a2-010a574aeaaf",
          "update_at": 1687656479880,
          "url": "https://authoring-modelarts.com/936bea3e-d3df-435e-8b58-d817283284ae/lab",
          "user": {
           "domain": {
            "id": "878991804cdc4ba597xxxxxxxxxx9dd9",
            "name": "hwstaff_test"
           },
           "id": "99250e439b33431081xxxxxxxxxxa885",
           "name": "test"
          },
          "user_id": "99250e439b33431081xxxxxxxxxxa885",
          "volume": {
           "category": "EFS",
           "ownership": "MANAGED",
           "mount_path": "/home/ma-user/work/",
           "capacity": 50,
           "read_only": false
          },
          "workspace_id": "0",
          "billing_items": []
         }

#. Call the API for :ref:`starting a notebook instance <startnotebook>` to restart the instance.

   a. Request body.

      URI: GET https://*{ma_endpoint}*/v1/*{project_id}*/notebooks/*{id}*/start

      Request header: X-auth-Token →\ **MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...**

      Set the bold parameters based on site requirements.

   b. Status code **200** is returned. The response body is as follows:

      .. code-block::

         {
          "create_at": 1687656452472,
          "data_volumes": [],
          "description": "api-test",
          "endpoints": [
           {
            "service": "NOTEBOOK",
            "uri": "https://authoring-modelarts.com/936bea3e-d3df-435e-8b58-d817283284ae/lab"
           }
          ],
          "feature": "NOTEBOOK",
          "flavor": "modelarts.vm.cpu.2u",
          "id": "936bea3e-d3df-435e-8b58-d817283284ae",
          "image": {
           "description": "",
           "id": "e1a07296-22a8-4f05-8bc8-e936c8e54090",
           "name": "notebook2.0-mul-kernel-cpu-cp36",
           "swr_path": "swr.com/atelier/notebook2.0-mul-kernel-cpu-cp36:5.0.1-release-v2-20220505",
           "tag": "5.0.1-release-v2-20220505",
           "type": "BUILD_IN"
          },
          "lease": {
           "create_at": 1687656452470,
           "duration": 6540099,
           "enable": true,
           "type": "TIMING",
           "update_at": 1687659392569
          },
          "name": "notebooks_test",
          "status": "STARTING",
          "tags": [],
          "token": "6f773860-21d4-9fe8-75c8-a38ea13ebf08",
          "update_at": 1687659203630,
          "url": "https://authoring-modelarts.com/936bea3e-d3df-435e-8b58-d817283284ae/lab",
          "user": {
           "domain": {
            "id": "878991804cdc4ba597xxxxxxxxxx9dd9",
            "name": "hwstaff_test"
           },
           "id": "99250e439b33431081xxxxxxxxxxa885",
           "name": "test"
          },
          "user_id": "99250e439b33431081xxxxxxxxxxa885",
          "volume": {
           "category": "EFS",
           "ownership": "MANAGED",
           "mount_path": "/home/ma-user/work/",
           "capacity": 50,
           "read_only": false
          },
          "workspace_id": "0",
          "billing_items": []
         }

#. Call the API for :ref:`deleting a notebook instance <deletenotebook>` to delete the instance that is no longer needed.

   a. Request body:

      URI: DELETE https://*{ma_endpoint}*/v1/*{project_id}*/notebooks/*{id}*

      Request header:

      -  X-auth-Token →\ **MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...**
      -  Content-Type →application/json

      Set the bold parameters based on site requirements.

   b. Status code **200** is returned, indicating that the instance is successfully deleted.
