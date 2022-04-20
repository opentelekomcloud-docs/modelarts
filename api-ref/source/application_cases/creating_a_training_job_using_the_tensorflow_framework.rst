.. _modelarts_03_0401:

Creating a Training Job Using the TensorFlow Framework
======================================================

Overview
--------

This section describes how to train a model on ModelArts by calling a series of APIs.

The process for creating a training job using the TensorFlow framework is as follows:

#. Call the API in :ref:`Authentication <modelarts_03_0004>` to obtain the user token, which will be put into the request header for authentication in a subsequent request.
#. Call the API in :ref:`Querying Job Resource Specifications <modelarts_03_0072>` to obtain the resource flavors available for training jobs.
#. Call the API in :ref:`Querying Job Engine Specifications <modelarts_03_0073>` to view the engine types and versions available for training jobs.
#. Call the API in :ref:`Creating a Training Job <modelarts_03_0045>` to create a training job.
#. Call the API in :ref:`Querying the Details About a Training Job Version <modelarts_03_0047>` to query the details about the training job based on the job ID.
#. Call the API in :ref:`Obtaining the Name of a Training Job Log File <modelarts_03_0054>` to obtain the name of the training job log file.
#. Call the API in :ref:`Querying Training Job Logs <modelarts_03_0149>` to view the log details of the training job.
#. Call the API in :ref:`Deleting a Training Job <modelarts_03_0053>` to delete the training job if it is no longer needed.

Prerequisites
-------------

-  You have obtained the endpoints of and :ref:`ModelArts <modelarts_03_0141>`.
-  You have located the region where the service is deployed and obtained .
-  You have obtained the project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`.
-  You have prepared the training code for TensorFlow. For example, you have stored the boot file **train_mnist_tf.py** in the **/test-modelarts/mnist-tensorflow-code/** directory of OBS.
-  You have prepared a dataset for the training job. For example, you have stored a training dataset in the **/test-modelarts/dataset-mnist/** directory of OBS.
-  You have created the output path of the training job, for example, **/test-modelarts/mnist-model/output/**.

Procedure
---------

#. .. _modelarts_03_0401__en-us_topic_0000001073831232_li1438114133315:

   Call the API in :ref:`Authentication <modelarts_03_0004>` to obtain the user token.

   a. Request body:

      URI format: POST https://**{iam_endpoint}**/v3/auth/tokens

      Request header: Content-Type → application/json

      Request body:

      .. code-block::

         {
           "auth": {
             "identity": {
               "methods": ["password"],
               "password": {
                 "user": {
                   "name": "username", 
                   "password": "**********",
                   "domain": {
                     "name": "domainname"  
                   }
                 }
               }
             },
             "scope": {
               "project": {
                 "name": ""  
               }
             }
           }
         }

      Set the italic fields in bold based on the site requirements.

      -  Replace **iam_endpoint** with the IAM endpoint.
      -  Replace **username** with the IAM username.
      -  Replace **\*******\*** with the login password of the user.
      -  Replace **domainname** with the account to which the user belongs.
      -  Replace with the project name, which indicates the zone where the service is deployed.

   b. The status code **201 Created** is returned. The value of **X-Subject-Token** in the response header is the token.

      .. code-block::

         x-subject-token →MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...

#. .. _modelarts_03_0401__en-us_topic_0000001073831232_li384513468342:

   Call the API in :ref:`Querying Job Resource Specifications <modelarts_03_0072>` to obtain the resource flavors available for training jobs.

   a. Request body:

      URI format: GET https://**{ma_endpoint}**/v1/**{project_id}**/job/resource-specs?job_type=train

      Request header: X-auth-Token →\ **MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...**

      Set the italic fields in bold based on the site requirements.

      -  Replace **ma_endpoint** with the ModelArts endpoint.
      -  Replace **project_id** with the project ID of the user.
      -  Set **X-auth-Token** to the token obtained in :ref:`1 <modelarts_03_0401__en-us_topic_0000001073831232_li1438114133315>`.

   b. The status code **200 OK** is returned. The response body is as follows:

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

      -  Select and record the flavor type required for creating the training job based on the **spec_code** field. This section uses **modelarts.vm.cpu.8u** as an example and records the value of the **max_num** field as **1**.
      -  The **no_resource** field is used to determine whether resources are sufficient. Value **false** indicates that resources are available.

#. .. _modelarts_03_0401__en-us_topic_0000001073831232_li12845104623418:

   Call the API in :ref:`Querying Job Engine Specifications <modelarts_03_0073>` to view the engine types and versions available for training jobs.

   a. Request body:

      URI format: GET https://**{ma_endpoint}**/v1/**{project_id}**/job/ai-engines?job_type=train

      Request header: X-auth-Token →\ **MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...**

      Set the italic fields in bold based on the site requirements.

      -  Replace **ma_endpoint** with the ModelArts endpoint.
      -  Replace **project_id** with the project ID of the user.
      -  Set **X-auth-Token** to the token obtained in :ref:`1 <modelarts_03_0401__en-us_topic_0000001073831232_li1438114133315>`.

   b. The status code **200 OK** is returned. The response body is as follows:

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

      Select the engine flavor required for creating a training job based on the **engine_name** and **engine_version** fields and record **engine_id**. This section describes how to create a job based on the TensorFlow engine. Record **engine_id** as **4**.

#. .. _modelarts_03_0401__en-us_topic_0000001073831232_li5845144683416:

   Call the API in :ref:`Creating a Training Job <modelarts_03_0045>` to create a training job named **jobtest_TF** based on the TensorFlow framework.

   a. Request body:

      URI format: POST https://**{ma_endpoint}**/v1/**{project_id}**/training-jobs

      Request header:

      -  X-auth-Token →\ **MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...**
      -  Content-Type →application/json

      Request body:

      .. code-block::

         {
             "job_name": "jobtest_TF",
             "job_desc": "using TensorFlow for handwritten digit recognition",
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

      Set the italic fields in bold based on the site requirements.

      -  Set **job_name** and **job_desc** to the name and description of the training job.
      -  Set **worker_server_num** and **code** to the values of **max_num** and **spec_code** obtained in :ref:`2 <modelarts_03_0401__en-us_topic_0000001073831232_li384513468342>`.
      -  Set **engine_id** to the engine ID obtained in :ref:`3 <modelarts_03_0401__en-us_topic_0000001073831232_li12845104623418>`.
      -  Set **train_url** to the output directory of the training job.
      -  Set **app_url** and **boot_file_url** to the code directory and code boot file of the training job, respectively.
      -  Set **data_url** to the dataset directory used by the training job.

   b. The status code **200 OK** is returned, indicating that the training job has been created. The response body is as follows:

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

      -  Record the values of **job_id** (training job ID) and **version_id** (training job version ID) for future use.
      -  The value of **status** is **1**, indicating that the training job is being initialized.

#. Call the API in :ref:`Querying the Details About a Training Job Version <modelarts_03_0047>` to query the details about the training job based on the job ID.

   a. Request body:

      URI format: GET https://**{ma_endpoint}**/v1/**{project_id}**/training-jobs/**567524**/versions/**1108482**

      Request header: X-auth-Token →\ **MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...**

      Set the italic fields in bold based on the site requirements.

      -  Replace *567524* with the value of **job_id** recorded in :ref:`4 <modelarts_03_0401__en-us_topic_0000001073831232_li5845144683416>`.
      -  Replace *1108482* with the value of **version_id** recorded in :ref:`4 <modelarts_03_0401__en-us_topic_0000001073831232_li5845144683416>`.

   b. The status code **200 OK** is returned. The response body is as follows:

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
           "job_desc": "using TensorFlow for handwritten digit recognition",
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

      You can learn about the version details of the training job based on the response. The value of **status** is **10**, indicating that the training job is successful.

#. .. _modelarts_03_0401__en-us_topic_0000001073831232_li52217241518:

   Call the API in :ref:`Obtaining the Name of a Training Job Log File <modelarts_03_0054>` to obtain the name of the training job log file.

   a. Request body:

      URI format: GET https://**{ma_endpoint}**/v1/**{project_id}**/training-jobs/**567524**/versions/**1108482**/log/file-names

      Request header: X-auth-Token →\ **MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...**

      Set the italic fields in bold based on the site requirements.

   b. The status code **200 OK** is returned. The response body is as follows:

      .. code-block::

         {
           "is_success": true,
           "log_file_list": [
             "job-jobtest-tf.0"
           ]
         }

      Only one log file named **job-jobtest-tf.0** exists.

#. Call the API in :ref:`Querying Training Job Logs <modelarts_03_0149>` to query details about eight rows in the training job log file.

   a. Request body:

      URI format: GET https://**{ma_endpoint}**/v1/**{project_id}**/training-jobs/**567524**/versions/**1108482**/aom-log?log_file=\ **job-jobtest-tf.0**\ &lines=\ **8**\ &order=\ **desc**

      Request header: X-auth-Token →\ **MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...**

      Set the italic fields in bold based on the site requirements.

      -  Set **log_file** to the name of the log file obtained in :ref:`6 <modelarts_03_0401__en-us_topic_0000001073831232_li52217241518>`.
      -  Set **lines** to the rows to be obtained in the log file.
      -  Set **order** to the log query direction.

   b. The status code **200 OK** is returned. The response body is as follows:

      .. code-block::

         {
           "start_line": "1609121886518240330",
           "lines": 8,
           "is_success": true,
           "end_line": "1609121900042593083",
           "content": "Done exporting!\n\n[Modelarts Service Log]Training completed.\n\n[ModelArts Service Log]modelarts-pipe: will create log file /tmp/log/jobtest_TF.log\n\n[ModelArts Service Log]modelarts-pipe: will create log file /tmp/log/jobtest_TF.log\n\n[ModelArts Service Log]modelarts-pipe: will write log file /tmp/log/jobtest_TF.log\n\n[ModelArts Service Log]modelarts-pipe: param for max log length: 1073741824\n\n[ModelArts Service Log]modelarts-pipe: param for whether exit on overflow: 0\n\n[ModelArts Service Log]modelarts-pipe: total length: 23303\n"
         }

#. Call the API in :ref:`Deleting a Training Job <modelarts_03_0053>` to delete the training job if it is no longer needed.

   a. Request body:

      URI format: GET https://**{ma_endpoint}**/v1/**{project_id}**/training-jobs/**567524**

      Request header: X-auth-Token →\ **MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...**

      Set the italic fields in bold based on the site requirements.

   b. The status code **200 OK** is returned, indicating that the job has been deleted. The response is as follows:

      .. code-block::

         {
           "is_success": true
         }
