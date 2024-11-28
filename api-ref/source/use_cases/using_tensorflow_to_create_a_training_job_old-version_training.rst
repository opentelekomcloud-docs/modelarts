:original_name: modelarts_03_0401.html

.. _modelarts_03_0401:

Using TensorFlow to Create a Training Job (Old-Version Training)
================================================================

This section describes how to train a model by calling ModelArts APIs.

Overview
--------

The process of creating a training job using TensorFlow is as follows:

#. Call the API for :ref:`authentication <modelarts_03_0004>` to obtain a user token, which will be added in a request header for authentication.
#. Call the API for :ref:`obtaining job resource specifications <modelarts_03_0072>` to obtain the resource flavors available for training jobs.
#. Call the API for :ref:`obtaining job engine specifications <modelarts_03_0073>` to obtain the engine types and versions available for training jobs.
#. Call the API for :ref:`creating a training job <modelarts_03_0045>` to create a training job.
#. Call the API for :ref:`obtaining the details about a training job version <modelarts_03_0047>` to obtain the details about the training job based on the job ID.
#. Call the API for :ref:`obtaining the name of a training job log file <modelarts_03_0054>` to obtain the log file name of the training job.
#. Call the API for :ref:`obtaining training job logs <modelarts_03_0149>` to obtain the log details of the training job.
#. Call the API for :ref:`deleting a training job <modelarts_03_0053>` to delete the training job if it is no longer needed.

Prerequisites
-------------

-  You have obtained the .
-  The following information is available: region where ModelArts is deployed, :ref:`project name and ID <modelarts_03_0147>`, :ref:`account name and ID <modelarts_03_0148>`, and :ref:`username and ID <modelarts_03_0006>`.

-  The TensorFlow training code is available, for example, by storing the boot file **train_mnist_tf.py** in **/test-modelarts/mnist-tensorflow-code/** on OBS.
-  A dataset for the training job is available, for example, by storing a training dataset in **/test-modelarts/dataset-mnist/** on OBS.
-  The output path of the training job has been specified, for example, **/test-modelarts/mnist-model/output/**.

Procedure
---------

#. .. _en-us_topic_0000001401866062__li384513468342:

   Call the API for :ref:`obtaining job resource specifications <modelarts_03_0072>` to obtain the resource flavors available for training jobs.

   a. Request body:

      URI: GET https://*{ma_endpoint}*/v1/*{project_id}*/job/resource-specs?job_type=train

      Request header: X-auth-Token →\ *MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...*

      Set the italic parameters based on site requirements.

      -  *ma_endpoint*: ModelArts endpoint
      -  *project_id*: Your project ID
      -  **X-auth-Token**: Token obtained in the previous step

   b. Response body with status code **200 OK** returned:

      .. code-block::

         {
           "specs": [
             ......
             {
               "spec_id": 7,
               "core": "2",
               "cpu": "8",
               "gpu_num": 0,
               "gpu_type": "",
               "spec_code": "modelarts.vm.cpu.2u",
               "unit_num": 1,
               "max_num": 1,
               "storage": "",
               "interface_type": 1,
               "no_resource": false
             },
             {
               "spec_id": 27,
               "core": "8",
               "cpu": "32",
               "gpu_num": 0,
               "gpu_type": "",
               "spec_code": "modelarts.vm.cpu.8u",
               "unit_num": 1,
               "max_num": 1,
               "storage": "",
               "interface_type": 1,
               "no_resource": false
             }
           ],
           "is_success": true,
           "spec_total_count": 5
         }

      -  Select and record the flavor type required for creating the training job based on **spec_code**. This section uses **modelarts.vm.cpu.8u** with **max_num** set to **1** as an example.
      -  **no_resource** specifies whether resources are sufficient. Value **false** indicates that resources are available.

#. .. _en-us_topic_0000001401866062__li12845104623418:

   Call the API for :ref:`obtaining job engine specifications <modelarts_03_0073>` to obtain the engine types and versions available for training jobs.

   a. Request body:

      URI: GET https://*{ma_endpoint}*/v1/*{project_id}*/job/ai-engines?job_type=train

      Request header: X-auth-Token →\ *MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...*

      Set the italic parameters based on site requirements.

   b. Response body with status code **200 OK** returned:

      .. code-block::

         {
           "engines": [
             {
               "engine_type": 13,
               "engine_name": "Ascend-Powered-Engine",
               "engine_id": 130,
               "engine_version": "TF-1.15-python3.7-aarch64"
             },
             ......
             {
               "engine_type": 1,
               "engine_name": "TensorFlow",
               "engine_id": 3,
               "engine_version": "TF-1.8.0-python2.7"
             },
             {
               "engine_type": 1,
               "engine_name": "TensorFlow",
               "engine_id": 4,
               "engine_version": "TF-1.8.0-python3.6"
             },
             ......
             {
               "engine_type": 9,
               "engine_name": "XGBoost-Sklearn",
               "engine_id": 100,
               "engine_version": "XGBoost-0.80-Sklearn-0.18.1-python3.6"
             }
           ],
           "is_success": true
         }

      Select the engine for creating a training job based on **engine_name** and **engine_version** and record **engine_id**. This section describes how to use TensorFlow to create a job with **engine_id** set to **4**.

#. .. _en-us_topic_0000001401866062__li5845144683416:

   Call the API for :ref:`creating a training job <modelarts_03_0045>` to create a TensorFlow training job named **jobtest_TF**.

   a. Request body:

      URI: POST https://*{ma_endpoint}*/v1/*{project_id}*/training-jobs

      Request header:

      -  X-auth-Token →\ *MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...*
      -  Content-Type →application/json

      Request body:

      .. code-block::

         {
             "job_name": "jobtest_TF",
             "job_desc": "Use TensorFlow to recognize handwritten digits.",
             "config": {
                 "worker_server_num": 1,
                 "parameter": [],
                 "flavor": {
                     "code": "modelarts.vm.cpu.8u"
                 },
                 "train_url": "/test-modelarts/mnist-model/output/",
                 "engine_id": 4,
                 "app_url": "/test-modelarts/mnist-tensorflow-code/",
                 "boot_file_url": "/test-modelarts/mnist-tensorflow-code/train_mnist_tf.py",
                 "data_source": [
                     {
                         "type": "obs",
                         "data_url": "/test-modelarts/dataset-mnist/"
                     }
                 ]
             },
             "notification": {
                 "topic_urn": "",
                 "events": []
             },
             "workspace_id": "0"
         }

      Set the italic parameters based on site requirements.

      -  **job_name** and **job_desc**: Name and description of the training job, respectively
      -  **worker_server_num** and **code**: **max_num** and **spec_code** values, respectively, obtained in :ref:`1 <en-us_topic_0000001401866062__li384513468342>`
      -  **engine_id**: Engine ID obtained in :ref:`2 <en-us_topic_0000001401866062__li12845104623418>`
      -  **train_url**: Output directory of the training job
      -  **app_url** and **boot_file_url**: Code directory and code boot file of the training job, respectively
      -  **data_url**: Dataset directory used by the training job

   b. Response body with status code **200 OK** returned (indicating that the training job has been created):

      .. code-block::

         {
           "version_name": "V0001",
           "job_name": "jobtest_TF",
           "create_time": 1609121837000,
           "job_id": 567524,
           "resource_id": "jobaedef089",
           "version_id": 1108482,
           "is_success": true,
           "status": 1
         }

      -  Record the values of **job_id** (training job ID) and **version_id** (training job version) for future use.
      -  **status** value **1** indicates the training job is being initialized.

#. Call the API for :ref:`obtaining the details about a training job version <modelarts_03_0047>` to obtain the details about the training job based on the job ID.

   a. Request body:

      URI: GET https://*{ma_endpoint}*/v1/*{project_id}*/training-jobs/*{job_id}*/versions/*{version_id}*

      Request header: X-auth-Token →\ *MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...*

      Set the italic parameters based on site requirements.

      -  **job_id**: Training job ID recorded in :ref:`3 <en-us_topic_0000001401866062__li5845144683416>`
      -  **version_id**: Training job version recorded in :ref:`3 <en-us_topic_0000001401866062__li5845144683416>`

   b. Response body with status code **200 OK** returned:

      .. code-block::

         {
           "dataset_name": null,
           "duration": 1326,
           "spec_code": "modelarts.vm.cpu.8u",
           "parameter": [],
           "start_time": 1609121913000,
           "model_outputs": [],
           "engine_name": "TensorFlow",
           "error_result": null,
           "gpu_type": "",
           "user_frame_image": null,
           "gpu": null,
           "dataset_id": null,
           "nas_mount_path": null,
           "task_summary": {},
           "max_num": 1,
           "model_metric_list": "{}",
           "is_zombie": null,
           "flavor_code": "modelarts.vm.cpu.8u",
           "gpu_num": 0,
           "train_url": "/test-modelarts/mnist-model/output/",
           "engine_type": 1,
           "job_name": "jobtest_TF",
           "nas_type": "efs",
           "outputs": null,
           "job_id": 567524,
           "data_url": "/test-modelarts/dataset-mnist/",
           "log_url": null,
           "boot_file_url": "/test-modelarts/mnist-tensorflow-code/train_mnist_tf.py",
           "volumes": null,
           "dataset_version_id": null,
           "algorithm_id": null,
           "worker_server_num": 1,
           "pool_type": "SYSTEM_DEFINED",
           "autosearch_config": null,
           "job_desc": "Use TensorFlow to recognize handwritten digits.",
           "inputs": null,
           "model_id": null,
           "dataset_version_name": null,
           "pool_name": "hec-train-pub-cpu",
           "engine_version": "TF-1.8.0-python3.6",
           "system_metric_list": {
             "recvBytesRate": [
               "0",
               "0"
             ],
             "cpuUsage": [
               "0",
               "0"
             ],
             "sendBytesRate": [
               "0",
               "0"
             ],
             "memUsage": [
               "0",
               "0"
             ],
             "gpuUtil": [
               "0",
               "0"
             ],
             "gpuMemUsage": [
               "0",
               "0"
             ],
             "interval": 1,
             "diskWriteRate": [
               "0",
               "0"
             ],
             "diskReadRate": [
               "0",
               "0"
             ]
           },
           "retrain_model_id": null,
           "version_name": "V0001",
           "pod_version": "1.8.0-cp36",
           "engine_id": 4,
           "status": 10,
           "cpu": "32",
           "user_image_url": null,
           "spec_id": 27,
           "is_success": true,
           "storage": "",
           "nas_share_addr": null,
           "version_id": 1108482,
           "no_resource": false,
           "user_command": null,
           "resource_id": "jobaedef089",
           "core": "8",
           "npu_info": null,
           "app_url": "/test-modelarts/mnist-tensorflow-code/",
           "data_source": [
             {
               "type": "obs",
               "data_url": "/test-modelarts/dataset-mnist/"
             }
           ],
           "pre_version_id": null,
           "create_time": 1609121837000,
           "job_type": 1,
           "pool_id": "pool7d1e384a"
         }

      Learn about the version details of the training job based on the response. **status** value **10** indicates the training job has been executed.

#. .. _en-us_topic_0000001401866062__li52217241518:

   Call the API for :ref:`obtaining the name of a training job log file <modelarts_03_0054>` to obtain the log file name of the training job.

   a. Request body:

      URI: GET https://*{ma_endpoint}*/v1/*{project_id}*/training-jobs/*{job_id}*/versions/*{version_id}*/log/file-names

      Request header: X-auth-Token →\ *MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...*

      Set the italic parameters based on site requirements.

   b. Response body with status code **200 OK** returned:

      .. code-block::

         {
           "is_success": true,
           "log_file_list": [
             "job-jobtest-tf.0"
           ]
         }

      Only the log file named **job-jobtest-tf.0** is available.

#. Call the API for :ref:`obtaining training job logs <modelarts_03_0149>` to obtain details about the next eight rows of logs in the log file.

   a. Request body:

      URI: GET https://*{ma_endpoint}*/v1/*{project_id}*/training-jobs/*{job_id}*/versions/*{version_id}*/aom-log?log_file=\ *job-jobtest-tf.0*\ &lines=\ *8*\ &order=\ *desc*

      Request header: X-auth-Token →\ *MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...*

      Set the italic parameters based on site requirements.

      -  **log_file**: Name of the log file obtained in :ref:`5 <en-us_topic_0000001401866062__li52217241518>`
      -  **lines**: Number of rows of logs to be obtained in the log file
      -  **order**: Log query direction

   b. Response body with status code **200 OK** returned:

      .. code-block::

         {
           "start_line": "1609121886518240330",
           "lines": 8,
           "is_success": true,
           "end_line": "1609121900042593083",
           "content": "Done exporting!\n\n[Modelarts Service Log]Training completed.\n\n[ModelArts Service Log]modelarts-pipe: will create log file /tmp/log/jobtest_TF.log\n\n[ModelArts Service Log]modelarts-pipe: will create log file /tmp/log/jobtest_TF.log\n\n[ModelArts Service Log]modelarts-pipe: will write log file /tmp/log/jobtest_TF.log\n\n[ModelArts Service Log]modelarts-pipe: param for max log length: 1073741824\n\n[ModelArts Service Log]modelarts-pipe: param for whether exit on overflow: 0\n\n[ModelArts Service Log]modelarts-pipe: total length: 23303\n"
         }

#. Call the API for :ref:`deleting a training job <modelarts_03_0053>` to delete the training job if it is no longer needed.

   a. Request body:

      URI: GET https://*{ma_endpoint}*/v1/*{project_id}*/training-jobs/*{job_id}*

      Request header: X-auth-Token →\ *MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...*

      Set the italic parameters based on site requirements.

   b. Response body with status code **200 OK** returned (indicating that the job has been deleted):

      .. code-block::

         {
           "is_success": true
         }
