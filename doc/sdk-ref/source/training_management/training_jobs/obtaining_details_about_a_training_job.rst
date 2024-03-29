:original_name: modelarts_04_0161.html

.. _modelarts_04_0161:

Obtaining Details About a Training Job
======================================

Sample Code
-----------

In ModelArts notebook, you do not need to enter authentication parameters for session authentication. For details about session authentication of other development environments, see :ref:`Session Authentication <modelarts_04_0123>`.

-  Method 1: Use the specified **job_id** and **version_id**.

   ::

      from modelarts.session import Session
      from modelarts.estimator import Estimator
      session = Session()
      estimator = Estimator(modelarts_session=session, job_id="182626", version_id="278813")
      job_info = estimator.get_job_info()

-  Method 2: Use the training job created in :ref:`Creating a Training Job <modelarts_04_0131>`.

   ::

      job_info = job_instance.get_job_info()

-  Method 3: Use the training job version object returned in :ref:`Querying the List of Training Job Versions <modelarts_04_0169>`.

   ::

      job_info = job_version_instance_list[0].get_job_info()

Parameter Description
---------------------

.. table:: **Table 1** Estimator request parameters

   +-------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory | Type   | Description                                                                                                                                                                                                                                                              |
   +===================+===========+========+==========================================================================================================================================================================================================================================================================+
   | modelarts_session | Yes       | Object | Session object. For details about the initialization method, see :ref:`Session Authentication <modelarts_04_0123>`.                                                                                                                                                      |
   +-------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | job_id            | Yes       | String | ID of a training job. Obtain **job_id** using the training job object generated in :ref:`Creating a Training Job <modelarts_04_0131>`, for example, **job_instance.job_id**, or from the response in :ref:`Obtaining Training Jobs <modelarts_04_0160>`.                 |
   +-------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version_id        | Yes       | String | Version ID of a training job. Obtain **version_id** using the training job object generated in :ref:`Creating a Training Job <modelarts_04_0131>`, for example, **job_instance.version_id**, or from the response in :ref:`Obtaining Training Jobs <modelarts_04_0160>`. |
   +-------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** **get_job_info** response parameters

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                      |
   +=======================+=======================+==================================================================================================================================================================================================+
   | error_msg             | String                | Error message when the API call fails.                                                                                                                                                           |
   |                       |                       |                                                                                                                                                                                                  |
   |                       |                       | This parameter is not included when the API call succeeds.                                                                                                                                       |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | error_code            | String                | Error code when the API fails to be called. For details, see `Error Codes <https://docs.otc.t-systems.com/modelarts/api-ref/common_parameters/error_codes.html>`__ in *ModelArts API Reference*. |
   |                       |                       |                                                                                                                                                                                                  |
   |                       |                       | This parameter is not included when the API call succeeds.                                                                                                                                       |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | is_success            | Boolean               | Whether the API call succeeds                                                                                                                                                                    |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | job_id                | Long                  | Training job ID                                                                                                                                                                                  |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | job_name              | String                | Training job name                                                                                                                                                                                |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | job_desc              | String                | Description of a training job                                                                                                                                                                    |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version_id            | Long                  | Version ID of a training job                                                                                                                                                                     |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version_name          | String                | Version name of a training job                                                                                                                                                                   |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | pre_version_id        | Long                  | Name of the previous version of a training job                                                                                                                                                   |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | engine_type           | Short                 | Engine type of a training job. The mapping between **engine_type** and **engine_name** is as follows:                                                                                            |
   |                       |                       |                                                                                                                                                                                                  |
   |                       |                       | -  **engine_type**: **1**, **engine_name**: **TensorFlow**                                                                                                                                       |
   |                       |                       | -  **engine_type**: **2**, **engine_name**: **MXNet**                                                                                                                                            |
   |                       |                       | -  **engine_type**: **3**, **engine_name**: **Ray**                                                                                                                                              |
   |                       |                       | -  **engine_type**: **4**, **engine_name**: **Caffe**                                                                                                                                            |
   |                       |                       | -  **engine_type**: **5**, **engine_name**: **Spark_MLlib**                                                                                                                                      |
   |                       |                       | -  **engine_type**: **9**, **engine_name**: **XGBoost-Sklearn**                                                                                                                                  |
   |                       |                       | -  **engine_type**: **10**, **engine_name**: **PyTorch**                                                                                                                                         |
   |                       |                       | -  **engine_type**: **12**, **engine_name**: **Horovod**                                                                                                                                         |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | engine_name           | String                | Name of the engine selected for a training job. Currently, the following engines are supported:                                                                                                  |
   |                       |                       |                                                                                                                                                                                                  |
   |                       |                       | -  Caffe                                                                                                                                                                                         |
   |                       |                       | -  Horovod                                                                                                                                                                                       |
   |                       |                       | -  MXNet                                                                                                                                                                                         |
   |                       |                       | -  PyTorch                                                                                                                                                                                       |
   |                       |                       | -  Ray                                                                                                                                                                                           |
   |                       |                       | -  Spark_MLlib                                                                                                                                                                                   |
   |                       |                       | -  TensorFlow                                                                                                                                                                                    |
   |                       |                       | -  XGBoost-Sklearn                                                                                                                                                                               |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | engine_id             | Long                  | ID of the engine selected for a training job                                                                                                                                                     |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | engine_version        | String                | Version of the engine selected for a training job                                                                                                                                                |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                | Integer               | Status of a training job. For details about job statuses, see :ref:`Job Statuses <modelarts_04_0077>`.                                                                                           |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | app_url               | String                | Code directory of a training job                                                                                                                                                                 |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | boot_file_url         | String                | Boot file of a training job                                                                                                                                                                      |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time           | Long                  | Time when a training job is created                                                                                                                                                              |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | parameter             | JSON Array            | Running parameters of a training job. It is a collection of label-value pairs. This parameter is a container environment variable when a job uses a custom image.                                |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | duration              | Long                  | Training job running duration, in milliseconds                                                                                                                                                   |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | spec_id               | Long                  | ID of the resource specifications selected for a training job                                                                                                                                    |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | core                  | String                | Number of cores of the resource specifications                                                                                                                                                   |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | cpu                   | String                | CPU memory of the resource specifications                                                                                                                                                        |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | gpu_num               | Integer               | Number of GPUs of the resource specifications                                                                                                                                                    |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | gpu_type              | String                | GPU type of the resource specifications                                                                                                                                                          |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | worker_server_num     | Integer               | Number of workers in a training job                                                                                                                                                              |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | data_url              | String                | Dataset of a training job                                                                                                                                                                        |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | train_url             | String                | OBS path to the training job output file                                                                                                                                                         |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dataset_version_id    | String                | Dataset version ID of a training job                                                                                                                                                             |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dataset_id            | String                | Dataset ID of a training job                                                                                                                                                                     |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | data_source           | JSON Array            | Datasets of a training job                                                                                                                                                                       |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | model_id              | Long                  | Model ID of a training job                                                                                                                                                                       |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | model_metric_list     | JSON Array            | Model metrics of a training job                                                                                                                                                                  |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | system_metric_list    | JSON Array            | System monitoring metrics of a training job                                                                                                                                                      |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | user_image_url        | String                | SWR URL of the custom image used by a training job                                                                                                                                               |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | user_command          | String                | Boot command used to start the container of the custom image of a training job                                                                                                                   |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** **data_source** parameters

   +-----------------------+-----------------------+-----------------------------------------------------+
   | Parameter             | Type                  | Description                                         |
   +=======================+=======================+=====================================================+
   | dataset_id            | String                | Dataset ID of a training job                        |
   +-----------------------+-----------------------+-----------------------------------------------------+
   | dataset_version       | String                | Dataset version ID of a training job                |
   +-----------------------+-----------------------+-----------------------------------------------------+
   | type                  | String                | Dataset type                                        |
   |                       |                       |                                                     |
   |                       |                       | **obs**: Data from OBS is used.                     |
   |                       |                       |                                                     |
   |                       |                       | **dataset**: Data from a specified dataset is used. |
   +-----------------------+-----------------------+-----------------------------------------------------+
   | data_url              | String                | OBS bucket path                                     |
   +-----------------------+-----------------------+-----------------------------------------------------+

.. table:: **Table 4** **model_metric_list** parameters

   ============ ========== ===============================================
   Parameter    Type       Description
   ============ ========== ===============================================
   metric       JSON Array Validation metrics of a class of a training job
   total_metric JSON Array All validation metrics of a training job
   ============ ========== ===============================================

.. table:: **Table 5** **system_metric_list** parameters

   ========= ========== ==============================
   Parameter Type       Description
   ========= ========== ==============================
   cpuUsage  JSON Array CPU usage of a training job
   memUsage  JSON Array Memory usage of a training job
   gpuUtil   JSON Array GPU usage of a training job
   ========= ========== ==============================

.. table:: **Table 6** **metric** parameters

   +---------------+------------+------------------------------------------------------------+
   | Parameter     | Type       | Description                                                |
   +===============+============+============================================================+
   | metric_values | JSON Array | Validation metrics of a class of a training job            |
   +---------------+------------+------------------------------------------------------------+
   | reserved_data | JSON Array | Reserved parameter                                         |
   +---------------+------------+------------------------------------------------------------+
   | metric_meta   | JSON Array | A class of a training job, including the class ID and name |
   +---------------+------------+------------------------------------------------------------+

.. table:: **Table 7** **metric_values** parameters

   ========= ========== ======================================
   Parameter Type       Description
   ========= ========== ======================================
   recall    JSON Array Recall of a class of a training job
   precision JSON Array Precision of a class of a training job
   accuracy  JSON Array Accuracy of a class of a training job
   ========= ========== ======================================

.. table:: **Table 8** **total_metric** parameters

   =================== ========== ========================================
   Parameter           Type       Description
   =================== ========== ========================================
   total_metric_meta   JSON Array Reserved parameter
   total_reserved_data JSON Array Reserved parameter
   total_metric_values JSON Array All validation metrics of a training job
   =================== ========== ========================================

.. table:: **Table 9** **total_metric_values** parameters

   ========= ===== =================================
   Parameter Type  Description
   ========= ===== =================================
   f1_score  Float F1 score of a training job
   recall    Float Total recall of a training job
   precision Float Total precision of a training job
   accuracy  Float Total accuracy of a training job
   ========= ===== =================================
