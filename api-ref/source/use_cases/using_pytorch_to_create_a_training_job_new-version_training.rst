:original_name: modelarts_03_0407.html

.. _modelarts_03_0407:

Using PyTorch to Create a Training Job (New-Version Training)
=============================================================

This section describes how to train a model by calling ModelArts APIs.

Overview
--------

The process for creating a training job using PyTorch is as follows:

#. Obtain a user token, which will be added in a request header for authentication.

#. Call the API for :ref:`obtaining general flavors supported by a training job <showtrainingjobflavors>` to obtain the required flavors.

#. Call the API for :ref:`obtaining the preset AI frameworks supported by a training job <showtrainingjobengines>` to view the engines and their versions supported by a training job.

#. .. _en-us_topic_0000002340898518__li33722031111515:

   Call the API for :ref:`creating an algorithm <createalgorithm>` to create an algorithm and record the algorithm ID.

#. .. _en-us_topic_0000002340898518__li62310211161:

   Call the API for :ref:`creating a training job <createtrainingjob>` to create a training job using the UUID returned by the created algorithm and record the job ID.

#. Call the API for :ref:`querying details about a training job <showtrainingjobdetails>` to query the job status using the job ID.

#. Call the API for :ref:`querying the logs of a specified task in a training job (OBS link) <showobsurloftrainingjoblogs>` to obtain the OBS path of the training job logs.

#. Call the API for :ref:`querying the running metrics of a specified task in a training job <showtrainingjobmetrics>` to view detailed metrics of the job.

#. Call the API for :ref:`deleting a training job <deletetrainingjob>` to delete the job if it is no longer needed.

Prerequisites
-------------

-  You have obtained the endpoints of .
-  The following information is available: region where ModelArts is deployed, :ref:`project ID and name <modelarts_03_0147>`, :ref:`account name and ID <modelarts_03_0148>`, and :ref:`username and user ID <modelarts_03_0006>`.

-  The training code of PyTorch is available. For example, the startup file **test-pytorch.py** has been stored in the **obs://cnnorth4-job-test-v2/pytorch/fast_example/code/cpu** directory of OBS.
-  A data file for the training job is available. For example, a training dataset has been stored in the **obs://cnnorth4-job-test-v2/pytorch/fast_example/data** directory of OBS.
-  A path for outputting the training job model has been created, for example, **obs://cnnorth4-job-test-v2/pytorch/fast_example/outputs**.
-  A path for outputting the training job logs has been created, for example, **obs://cnnorth4-job-test-v2/pytorch/fast_example/log**.

Procedure
---------

#. .. _en-us_topic_0000002340898518__li676316281367:

   Call the API for :ref:`obtaining general flavors supported by a training job <showtrainingjobflavors>` to obtain the required flavors.

   a. Request body:

      URI: GET https://*{ma_endpoint}*/v2/*{project_id}*/ training-job-flavors? flavor_type=CPU

      Request header: X-Auth-Token →\ **MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...**

      Set the following parameters based on site requirements:

      -  *ma_endpoint*: ModelArts endpoint
      -  *project_id*: user's project ID
      -  **X-auth-Token**: token obtained in the previous step

   b. Status code **200** is returned. The response body is as follows:

      .. code-block::

         {
           "total_count": 2,
           "flavors": [
             {
               "flavor_id": "modelarts.vm.cpu.2u",
               "flavor_name": "Computing CPU(2U) instance",
               "flavor_type": "CPU",
               "billing": {
                 "code": "modelarts.vm.cpu.2u",
                 "unit_num": 1
               },
               "flavor_info": {
                 "max_num": 1,
                 "cpu": {
                   "arch": "x86",
                   "core_num": 2
                 },
                 "memory": {
                   "size": 8,
                   "unit": "GB"
                 },
                 "disk": {
                   "size": 50,
                   "unit": "GB"
                 }
               }
             },
             {
               "flavor_id": "modelarts.vm.cpu.8u",
               "flavor_name": "Computing CPU(8U) instance",
               "flavor_type": "CPU",
               "billing": {
                 "code": "modelarts.vm.cpu.8u",
                 "unit_num": 1
               },
               "flavor_info": {
                 "max_num": 16,
                 "cpu": {
                   "arch": "x86",
                   "core_num": 8
                 },
                 "memory": {
                   "size": 32,
                   "unit": "GB"
                 },
                 "disk": {
                   "size": 50,
                   "unit": "GB"
                 }
               }
             }
           ]
         }

      -  Select and record the flavor required for creating the training job based on the **flavor_id** value. This section uses flavor **modelarts.vm.cpu.8u** with its **max_num** set to **16** as an example.

#. .. _en-us_topic_0000002340898518__li1750593718369:

   Call the API for :ref:`obtaining the preset AI frameworks supported by a training job <showtrainingjobengines>` to view the engines and their versions supported by a training job.

   a. Request body:

      URI: GET https://*{ma_endpoint}*/v2/*{project_id}*/job/ training-job-engines

      Request header:

      X-Auth-Token→\ **MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...**

      Content-Type →application/json

      Set the bold parameters based on site requirements.

   b. Status code **200** is returned. The response body is as follows (only part of the response body is displayed because there are many engines):

      .. code-block::

         {
             "total": 28,
             "items": [
                 ......
                 {
                     "engine_id": "mindspore_1.6.0-cann_5.0.3.6-py_3.7-euler_2.8.3-aarch64",
                     "engine_name": "Powered-Engine",
                     "engine_version": "mindspore_1.6.0-cann_5.0.3.6-py_3.7-euler_2.8.3-aarch64",
                     "v1_compatible": false,
                     "run_user": "1000",
                     "image_info": {
                         "cpu_image_url": "",
                         "gpu_image_url": "atelier/mindspore_1_6_0:train",
                         "image_version": "mindspore_1.6.0-cann_5.0.3.6-py_3.7-euler_2.8.3-aarch64-snt9-roma-20211231193205-33131ee"
                     }
                 },
                 ......
                 {
                     "engine_id": "pytorch_1.8.0-cuda_10.2-py_3.7-ubuntu_18.04-x86_64",
                     "engine_name": "PyTorch",
                     "engine_version": "pytorch_1.8.0-cuda_10.2-py_3.7-ubuntu_18.04-x86_64",
                     "tags": [
                         {
                             "key": "auto_search",
                             "value": "True"
                         }
                     ],
                     "v1_compatible": false,
                     "run_user": "1102",
                     "image_info": {
                         "cpu_image_url": "aip/pytorch_1_8:train",
                         "gpu_image_url": "aip/pytorch_1_8:train",
                         "image_version": "pytorch_1.8.0-cuda_10.2-py_3.7-ubuntu_18.04-x86_64-20210912152543-1e0838d"
                     }
                 },
                 ......
                 {
                     "engine_id": "tensorflow_2.1.0-cuda_10.1-py_3.7-ubuntu_18.04-x86_64",
                     "engine_name": "TensorFlow",
                     "engine_version": "tensorflow_2.1.0-cuda_10.1-py_3.7-ubuntu_18.04-x86_64",
                     "tags": [
                         {
                             "key": "auto_search",
                             "value": "True"
                         }
                     ],
                     "v1_compatible": false,
                     "run_user": "1102",
                     "image_info": {
                         "cpu_image_url": "aip/tensorflow_2_1:train",
                         "gpu_image_url": "aip/tensorflow_2_1:train",
                         "image_version": "tensorflow_2.1.0-cuda_10.1-py_3.7-ubuntu_18.04-x86_64-20210912152543-1e0838d"
                     }
                 },
                 ......
             ]
         }

      Select the engine flavor required for creating a training job based on the **engine_name** and **engine_version** fields, and record the field values. This section uses the PyTorch engine as an example to describe how to create a job. In this example, the **engine_name** value is **PyTorch**, and the **engine_version** value is **pytorch_1.8.0-cuda_10.2-py_3.7-ubuntu_18.04-x86_64**.

#. Call the API for :ref:`creating an algorithm <createalgorithm>` to create an algorithm and record the algorithm ID.

   a. Request body:

      URI: POST https://*{ma_endpoint}*/v2/*{project_id}*/ algorithms

      Request header:

      X-Auth-Token→\ **MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...**

      Content-Type →application/json

      Set the bold parameters based on site requirements.

      Request body:

      .. code-block::

         {
             "metadata": {
                 "name": "test-pytorch-cpu",
                 "description": "test pytorch job in cpu in mode gloo"
             },
             "job_config": {
                 "boot_file": "/cnnorth4-job-test-v2/pytorch/fast_example/code/cpu/test-pytorch.py",
                 "code_dir": "/cnnorth4-job-test-v2/pytorch/fast_example/code/cpu/",
                 "engine": {
                     "engine_name": "PyTorch",
                     "engine_version": "pytorch_1.8.0-cuda_10.2-py_3.7-ubuntu_18.04-x86_64"
                 },
                 "inputs": [{
                     "name": "data_url",
                     "description": "Data source 1"
                 }],
                 "outputs": [{
                     "name": "train_url",
                     "description": "Output data 1"
                 }],
                 "parameters": [{
                         "name": "dist",
                         "description": "",
                         "value": "False",
                         "constraint": {
                             "editable": true,
                             "required": false,
                             "sensitive": false,
                             "type": "Boolean",
                             "valid_range": [],
                             "valid_type": "None"
                         }
                     },
                     {
                         "name": "world_size",
                         "description": "",
                         "value": "1",
                         "constraint": {
                             "editable": true,
                             "required": false,
                             "sensitive": false,
                             "type": "Integer",
                             "valid_range": [],
                             "valid_type": "None"
                         }
                     }
                 ],
                 "parameters_customization": true
             },
             "resource_requirements": []
         }

      Set the following parameters based on site requirements:

      -  **name** and **description** in the **metadata** field indicate the algorithm name and description, respectively.
      -  **code_dir** and **boot_file** in the **job_config** field indicate the code directory and code startup file of the algorithm, respectively. The code directory is the level-1 directory of the code startup file.
      -  **inputs** and **outputs** in the **job_config** field indicate the input and output of the algorithm, respectively. You can specify **data_url** and **train_url** based on the instance, and parse hyperparameters in the code to specify the local path of the data file required for training and the local output path of the model generated during training.

      -  **parameters_customization** in the **job_config** field indicates whether to support custom hyperparameters. Set this parameter to **true**.
      -  **parameters** in the **job_config** field indicates the hyperparameters of the algorithm. Set **name** to the hyperparameter name (a maximum of 64 characters, including uppercase letters, lowercase letters, digits, underscores (_), and hyphens (-)). Set **value** to the default value of the hyperparameter. Set **constraint** to the constraints of the hyperparameter. For example, set **type** to **String** (**String**, **Integer**, **Float**, and **Boolean** are supported), set **editable** to **true**, and set **required** to **false**.
      -  **engine** in the **job_config** field indicates the engine on which the algorithm depends. Use the **engine_name** and **engine_version** values recorded in :ref:`2 <en-us_topic_0000002340898518__li1750593718369>`.

   b. Status code **200 OK** is returned, indicating that the algorithm is successfully created. The response body is as follows:

      .. code-block::

         {
             "metadata": {
                 "id": "01c399ae-8593-4ef5-9e4d-085950aacde1",
                 "name": "test-pytorch-cpu",
                 "description": "test pytorch job in cpu in mode gloo",
                 "create_time": 1641890623262,
                 "workspace_id": "0",
                 "ai_project": "default-ai-project",
                 "user_name": "",
                 "domain_id": "0659fbf6de00109b0ff1c01fc037d240",
                 "source": "custom",
                 "api_version": "",
                 "is_valid": true,
                 "state": "",
                 "size": 4790,
                 "tags": null,
                 "attr_list": null,
                 "version_num": 0,
                 "update_time": 0
             },
             "share_info": {},
             "job_config": {
                 "code_dir": "/cnnorth4-job-test-v2/pytorch/fast_example/code/cpu/",
                 "boot_file": "/cnnorth4-job-test-v2/pytorch/fast_example/code/cpu/test-pytorch.py",
                 "parameters": [
                     {
                         "name": "dist",
                         "description": "",
                         "i18n_description": null,
                         "value": "False",
                         "constraint": {
                             "type": "Boolean",
                             "editable": true,
                             "required": false,
                             "sensitive": false,
                             "valid_type": "None",
                             "valid_range": []
                         }
                     },
                     {
                         "name": "world_size",
                         "description": "",
                         "i18n_description": null,
                         "value": "1",
                         "constraint": {
                             "type": "Integer",
                             "editable": true,
                             "required": false,
                             "sensitive": false,
                             "valid_type": "None",
                             "valid_range": []
                         }
                     }
                 ],
                 "parameters_customization": true,
                 "inputs": [
                     {
                         "name": "data_url",
                         "description": "Data source 1"
                     }
                 ],
                 "outputs": [
                     {
                         "name": "train_url",
                         "description": "Output data 1"
                     }
                 ],
                 "engine": {
                     "engine_id": "pytorch_1.8.0-cuda_10.2-py_3.7-ubuntu_18.04-x86_64",
                     "engine_name": "PyTorch",
                     "engine_version": "pytorch_1.8.0-cuda_10.2-py_3.7-ubuntu_18.04-x86_64",
                     "tags": [
                         {
                             "key": "auto_search",
                             "value": "True"
                         }
                     ],
                     "v1_compatible": false,
                     "run_user": "1102",
                     "image_info": {
                         "cpu_image_url": "aip/pytorch_1_8:train",
                         "gpu_image_url": "aip/pytorch_1_8:train",
                         "image_version": "pytorch_1.8.0-cuda_10.2-py_3.7-ubuntu_18.04-x86_64-20210912152543-1e0838d"
                     }
                 },
                 "code_tree": {
                     "name": "cpu/",
                     "children": [
                         {
                             "name": "test-pytorch.py"
                         }
                     ]
                 }
             },
             "resource_requirements": [],
             "advanced_config": {}
         }

      Record the value of **id** (algorithm ID, 32-bit UUID) in the **metadata** field for subsequent steps.

#. Call the API for :ref:`creating a training job <createtrainingjob>` to create a training job using the UUID returned by the created algorithm and record the job ID.

   a. Request body:

      URI: POST https://*{ma_endpoint}*/v2/*{project_id}*/training-jobs

      Request header:

      -  X-Auth-Token →\ **MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...**
      -  Content-Type →application/json

      Set the bold parameters based on site requirements.

      Request body:

      .. code-block::

         {
             "kind": "job",
             "metadata": {
                 "name": "test-pytorch-cpu01",
                 "description": "test pytorch work cpu in mode gloo"
             },
             "algorithm": {
                 "id": "01c399ae-8593-4ef5-9e4d-085950aacde1",
                 "parameters": [{
                         "name": "dist",
                         "value": "False"
                     },
                     {
                         "name": "world_size",
                         "value": "1"
                     }
                 ],
                 "inputs": [{
                     "name": "data_url",
                     "remote": {
                         "obs": {
                             "obs_url": "/cnnorth4-job-test-v2/pytorch/fast_example/data/"
                         }
                     }
                 }],
                 "outputs": [{
                     "name": "train_url",
                     "remote": {
                         "obs": {
                             "obs_url": "/cnnorth4-job-test-v2/pytorch/fast_example/outputs/"
                         }
                     }
                 }]
             },
             "spec": {
                 "resource": {
                     "flavor_id": "modelarts.vm.cpu.8u",
                     "node_count": 1
                 },
                 "log_export_path": {
                     "obs_url": "/cnnorth4-job-test-v2/pytorch/fast_example/log/"
                 }
             }
         }

      Set the following parameters based on site requirements:

      -  Set **kind** to the type of the training job. The default value is **job**.
      -  Set **name** and **description** in the **metadata** field to the name and description of the training job.
      -  Set **id** in the **algorithm** field to the algorithm ID obtained in :ref:`4 <en-us_topic_0000002340898518__li33722031111515>`.
      -  Set **inputs** and **outputs** in the **algorithm** field to the information about the input and output URLs of the training job. In this example, **obs_url** in **remote** of the **inputs** parameter indicates the OBS path for selecting the training data from the OBS bucket. **obs_url** in **remote** of the **outputs** parameter indicates the OBS path for storing the training output.
      -  Set **flavor_id** in the **spec** field to the flavor on which the training job depends. Use the **flavor_id** recorded in :ref:`1 <en-us_topic_0000002340898518__li676316281367>`. **node_count** indicates whether to use multi-node training (distributed training). Set it to **1** for a single-node training by default. **log_export_path** specifies the OBS path to which logs are uploaded.

   b. Status code **201 Created** is returned, indicating that the training job has been created. The response body is as follows:

      .. code-block::

         {
             "kind": "job",
             "metadata": {
                 "id": "66ff6991-fd66-40b6-8101-0829a46d3731",
                 "name": "test-pytorch-cpu01",
                 "description": "test pytorch work cpu in mode gloo",
                 "create_time": 1641892642625,
                 "workspace_id": "0",
                 "ai_project": "default-ai-project",
                 "user_name": "",
                 "annotations": {
                     "job_template": "Template DL",
                     "key_task": "worker"
                 }
             },
             "status": {
                 "phase": "Creating",
                 "secondary_phase": "Creating",
                 "duration": 0,
                 "start_time": 0,
                 "node_count_metrics": null,
                 "tasks": [
                     "worker-0"
                 ]
             },
             "algorithm": {
                 "id": "01c399ae-8593-4ef5-9e4d-085950aacde1",
                 "name": "test-pytorch-cpu",
                 "code_dir": "/cnnorth4-job-test-v2/pytorch/fast_example/code/cpu/",
                 "boot_file": "/cnnorth4-job-test-v2/pytorch/fast_example/code/cpu/test-pytorch.py",
                 "parameters": [
                     {
                         "name": "dist",
                         "description": "",
                         "i18n_description": null,
                         "value": "False",
                         "constraint": {
                             "type": "Boolean",
                             "editable": true,
                             "required": false,
                             "sensitive": false,
                             "valid_type": "None",
                             "valid_range": []
                         }
                     },
                     {
                         "name": "world_size",
                         "description": "",
                         "i18n_description": null,
                         "value": "1",
                         "constraint": {
                             "type": "Integer",
                             "editable": true,
                             "required": false,
                             "sensitive": false,
                             "valid_type": "None",
                             "valid_range": []
                         }
                     }
                 ],
                 "parameters_customization": true,
                 "inputs": [
                     {
                         "name": "data_url",
                         "description": "Data source 1",
                         "local_dir": "/home/ma-user/modelarts/inputs/data_url_0",
                         "remote": {
                             "obs": {
                                 "obs_url": "/cnnorth4-job-test-v2/pytorch/fast_example/data/"
                             }
                         }
                     }
                 ],
                 "outputs": [
                     {
                         "name": "train_url",
                         "description": "Output data 1",
                         "local_dir": "/home/ma-user/modelarts/outputs/train_url_0",
                         "remote": {
                             "obs": {
                                 "obs_url": "/cnnorth4-job-test-v2/pytorch/fast_example/outputs/"
                             }
                         },
                         "mode": "upload_periodically",
                         "period": 30
                     }
                 ],
                 "engine": {
                     "engine_id": "pytorch_1.8.0-cuda_10.2-py_3.7-ubuntu_18.04-x86_64",
                     "engine_name": "PyTorch",
                     "engine_version": "pytorch_1.8.0-cuda_10.2-py_3.7-ubuntu_18.04-x86_64",
                     "usage": "training",
                     "support_groups": "public",
                     "tags": [
                         {
                             "key": "auto_search",
                             "value": "True"
                         }
                     ],
                     "v1_compatible": false,
                     "run_user": "1102"
                 }
             },
             "spec": {
                 "resource": {
                     "flavor_id": "modelarts.vm.cpu.8u",
                     "flavor_name": "Computing CPU(8U) instance",
                     "node_count": 1,
                     "flavor_detail": {
                         "flavor_type": "CPU",
                         "billing": {
                             "code": "modelarts.vm.cpu.8u",
                             "unit_num": 1
                         },
                         "flavor_info": {
                             "cpu": {
                                 "arch": "x86",
                                 "core_num": 8
                             },
                             "memory": {
                                 "size": 32,
                                 "unit": "GB"
                             },
                             "disk": {
                                 "size": 50,
                                 "unit": "GB"
                             }
                         }
                     }
                 },
                 "log_export_path": {
                     "obs_url": "/cnnorth4-job-test-v2/pytorch/fast_example/log/"
                 },
                 "is_hosted_log": true
             }
         }

      -  Record the **id** value (training job ID) in the **metadata** field for subsequent steps.
      -  **phase** and **secondary_phase** under **Status** indicate the status and next status of the training job, respectively. In the example, **Creating** indicates that the training job is being created.

#. Call the API for :ref:`querying details about a training job <showtrainingjobdetails>` to query the job status using the job ID.

   a. Request body:

      URI: GET https://*{ma_endpoint}*/v2/*{project_id}*/training-jobs/**{training_job_id}**

      Request header: X-Auth-Token →\ **MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...**

      Set the following parameter based on site requirements:

      Set **training_job_id** to the training job ID recorded in :ref:`5 <en-us_topic_0000002340898518__li62310211161>`.

   b. Status code **200 OK** is returned. The response body is as follows:

      .. code-block::

         {
             "kind": "job",
             "metadata": {
                 "id": "66ff6991-fd66-40b6-8101-0829a46d3731",
                 "name": "test-pytorch-cpu01",
                 "description": "test pytorch work cpu in mode gloo",
                 "create_time": 1641892642625,
                 "workspace_id": "0",
                 "ai_project": "default-ai-project",
                 "user_name": "hwstaff_z00424192",
                 "annotations": {
                     "job_template": "Template DL",
                     "key_task": "worker"
                 }
             },
             "status": {
                 "phase": "Running",
                 "secondary_phase": "Running",
                 "duration": 268000,
                 "start_time": 1641892655000,
                 "node_count_metrics": [
                     [
                         1641892645000,
                         0
                     ],
                     [
                         1641892654000,
                         0
                     ],
                     [
                         1641892655000,
                         1
                     ],
                     [
                         1641892922000,
                         1
                     ],
                     [
                         1641892923000,
                         1
                     ]
                 ],
                 "tasks": [
                     "worker-0"
                 ]
             },
             "algorithm": {
                 "id": "01c399ae-8593-4ef5-9e4d-085950aacde1",
                 "name": "test-pytorch-cpu",
                 "code_dir": "/cnnorth4-job-test-v2/pytorch/fast_example/code/cpu/",
                 "boot_file": "/cnnorth4-job-test-v2/pytorch/fast_example/code/cpu/test-pytorch.py",
                 "parameters": [
                     {
                         "name": "dist",
                         "description": "",
                         "i18n_description": null,
                         "value": "False",
                         "constraint": {
                             "type": "Boolean",
                             "editable": true,
                             "required": false,
                             "sensitive": false,
                             "valid_type": "None",
                             "valid_range": []
                         }
                     },
                     {
                         "name": "world_size",
                         "description": "",
                         "i18n_description": null,
                         "value": "1",
                         "constraint": {
                             "type": "Integer",
                             "editable": true,
                             "required": false,
                             "sensitive": false,
                             "valid_type": "None",
                             "valid_range": []
                         }
                     }
                 ],
                 "parameters_customization": true,
                 "inputs": [
                     {
                         "name": "data_url",
                         "description": "Data source 1",
                         "local_dir": "/home/ma-user/modelarts/inputs/data_url_0",
                         "remote": {
                             "obs": {
                                 "obs_url": "/cnnorth4-job-test-v2/pytorch/fast_example/data/"
                             }
                         }
                     }
                 ],
                 "outputs": [
                     {
                         "name": "train_url",
                         "description": "Output data 1",
                         "local_dir": "/home/ma-user/modelarts/outputs/train_url_0",
                         "remote": {
                             "obs": {
                                 "obs_url": "/cnnorth4-job-test-v2/pytorch/fast_example/outputs/"
                             }
                         },
                         "mode": "upload_periodically",
                         "period": 30
                     }
                 ],
                 "engine": {
                     "engine_id": "pytorch_1.8.0-cuda_10.2-py_3.7-ubuntu_18.04-x86_64",
                     "engine_name": "PyTorch",
                     "engine_version": "pytorch_1.8.0-cuda_10.2-py_3.7-ubuntu_18.04-x86_64",
                     "usage": "training",
                     "support_groups": "public",
                     "tags": [
                         {
                             "key": "auto_search",
                             "value": "True"
                         }
                     ],
                     "v1_compatible": false,
                     "run_user": "1102"
                 }
             },
             "spec": {
                 "resource": {
                     "flavor_id": "modelarts.vm.cpu.8u",
                     "flavor_name": "Computing CPU(8U) instance",
                     "node_count": 1,
                     "flavor_detail": {
                         "flavor_type": "CPU",
                         "billing": {
                             "code": "modelarts.vm.cpu.8u",
                             "unit_num": 1
                         },
                         "flavor_info": {
                             "cpu": {
                                 "arch": "x86",
                                 "core_num": 8
                             },
                             "memory": {
                                 "size": 32,
                                 "unit": "GB"
                             },
                             "disk": {
                                 "size": 50,
                                 "unit": "GB"
                             }
                         }
                     }
                 },
                 "log_export_path": {
                     "obs_url": "/cnnorth4-job-test-v2/pytorch/fast_example/log/"
                 },
                 "is_hosted_log": true
             }
         }

      You can learn about the version details of the training job based on the response. The **status** value is **Running**, indicating that the training job is running.

#. Call the API for :ref:`querying the logs of a specified task in a training job (OBS link) <showobsurloftrainingjoblogs>` to obtain the OBS path of the training job logs.

   a. Request body:

      URI format: GET https://*{ma_endpoint}*/v2/*{project_id}*/training-jobs/*{training_job_id}*/tasks/*{task_id}*/logs/url

      Request header:

      X-Auth-Token→\ **MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...**

      Content-Type→\ **text/plain**

      Set the following parameters based on site requirements:

      -  **task_id** indicates the name of the training job. Generally, set it to **work-0**.
      -  **Content-Type** can be set either to **text/plain** or **application/octet-stream**. **text/plain** indicates that a temporary OBS preview URL is returned. **application/octet-stream** indicates that a temporary OBS download URL is returned.

   b. Status code **200 OK** is returned.

      The returned field indicates the OBS path of logs. You can copy the value to the browser to view the result.

#. Call the API for :ref:`querying the running metrics of a specified task in a training job <showtrainingjobmetrics>` to view detailed metrics of the job.

   a. Request body:

      URI format: GET https://*{ma_endpoint}*/v2/*{project_id}*/training-jobs/*{training_job_id}*/metrics/*{task_id}*

      Request header: X-Auth-Token →\ **MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...**

      Set the bold parameters based on site requirements.

   b. Status code **200 OK** is returned. The response body is as follows:

      .. code-block::

         {
             "metrics": [
                 {
                     "metric": "cpuUsage",
                     "value": [
                         -1,
                         -1,
                         28.622,
                         35.053,
                         39.988,
                         40.069,
                         40.082,
                         40.094
                     ]
                 },
                 {
                     "metric": "memUsage",
                     "value": [
                         -1,
                         -1,
                         0.544,
                         0.641,
                         0.736,
                         0.737,
                         0.738,
                         0.739
                     ]
                 },
                 {
                     "metric": "npuUtil",
                     "value": [
                         -1,
                         -1,
                         -1,
                         -1,
                         -1,
                         -1,
                         -1,
                         -1
                     ]
                 },
                 {
                     "metric": "npuMemUsage",
                     "value": [
                         -1,
                         -1,
                         -1,
                         -1,
                         -1,
                         -1,
                         -1,
                         -1
                     ]
                 },
                 {
                     "metric": "gpuUtil",
                     "value": [
                         -1,
                         -1,
                         -1,
                         -1,
                         -1,
                         -1,
                         -1,
                         -1
                     ]
                 },
                 {
                     "metric": "gpuMemUsage",
                     "value": [
                         -1,
                         -1,
                         -1,
                         -1,
                         -1,
                         -1,
                         -1,
                         -1
                     ]
                 }
             ]
         }

      You can view the metrics such as the CPU usage.

#. Call the API for :ref:`deleting a training job <deletetrainingjob>` to delete the job if it is no longer needed.

   a. Request body:

      URI: DELETE https://*{ma_endpoint}*/v2/*{project_id}*/training-jobs/*{training_job_id}*

      Request header: X-Auth-Token →\ **MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...**

      Set the bold parameters based on site requirements.

   b. Status code **202 No Content** is returned, indicating that the job is successfully deleted.
