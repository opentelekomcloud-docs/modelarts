:original_name: modelarts_04_0178.html

.. _modelarts_04_0178:

Modifying a Training Job Configuration
======================================

Sample Code
-----------

In ModelArts notebook, you do not need to enter authentication parameters for session authentication. For details about session authentication of other development environments, see :ref:`Session Authentication <modelarts_04_0123>`.

-  Example 1: Modify a training job parameter configuration using the data stored on OBS.

   ::

      from modelarts.session import Session
      from modelarts.estimator import Estimator
      session = Session()
      estimator = Estimator(
                            modelarts_session=session,
                            framework_type='PyTorch',                                     # AI engine name
                            framework_version='PyTorch-1.0.0-python3.6',                  # AI engine version
                            code_dir='/bucket/src/',                                      # Training script directory
                            boot_file='/bucket/src/pytorch_sentiment.py',                 # Training boot script directory
                            log_url='/bucket/log/',                                       # Training log directory
                            hyperparameters=[
                                             {"label":"classes",
                                              "value": "10"},
                                             {"label":"lr",
                                              "value": "0.001"}
                                             ],
                            output_path='/bucket/output/',                                 # Training output directory
                            train_instance_type='modelarts.vm.gpu.p100',                   # Training environment flavor
                            train_instance_count=1)                                        # Number of training nodes
      update_info = estimator.update_job_configs(config_name='my_job_config', inputs='/bucket/dataset/', config_desc='update')

-  Example 2: Modify a training job parameter configuration using a dataset.

   ::

      from modelarts.session import Session
      from modelarts.estimator import Estimator
      session = Session()
      estimator = Estimator(
                            modelarts_session=session,
                            framework_type='PyTorch',                                     # AI engine name
                            framework_version='PyTorch-1.0.0-python3.6',                  # AI engine version
                            code_dir='/bucket/src/',                                      # Training script directory
                            boot_file='/bucket/src/pytorch_sentiment.py',                 # Training boot script directory
                            log_url='/bucket/log/',                                       # Training log directory
                            hyperparameters=[
                                             {"label":"classes",
                                              "value": "10"},
                                             {"label":"lr",
                                              "value": "0.001"}
                                             ],
                            output_path='/bucket/output/',                                 # Training output directory
                            train_instance_type='modelarts.vm.gpu.p100',                   # Training environment flavor
                            train_instance_count=1)                                        # Number of training nodes
      update_info = estimator.update_job_configs(config_name='my_job_config', dataset_id='4AZNvFkN7KYr5EdhFkH', dataset_version_id='UOF9BIeSGArwVt0oI6T', config_desc='update')

Parameter Description
---------------------

.. table:: **Table 1** Estimator request parameters

   +----------------------+-----------+------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter            | Mandatory | Type       | Description                                                                                                                                                                                               |
   +======================+===========+============+===========================================================================================================================================================================================================+
   | modelarts_session    | Yes       | Object     | Session object. For details about the initialization method, see :ref:`Session Authentication <modelarts_04_0123>`.                                                                                       |
   +----------------------+-----------+------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | train_instance_count | Yes       | Long       | Number of workers in a training job                                                                                                                                                                       |
   +----------------------+-----------+------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | code_dir             | No        | String     | Code directory of a training job, for example, **/bucket/src/**. Leave this parameter blank when **model_name** is set.                                                                                   |
   +----------------------+-----------+------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | boot_file            | No        | String     | Boot file of a training job, which needs to be stored in the code directory. For example, **/bucket/src/boot.py**. Leave this parameter blank when **model_name** is set.                                 |
   +----------------------+-----------+------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | model_name           | No        | Long       | Name of the built-in algorithm used by a training job. If you have configured **model_name**, you do not need to configure **app_url**, **boot_file_url**, **framework_type**, and **framework_version**. |
   +----------------------+-----------+------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | output_path          | Yes       | String     | Output path of a training job                                                                                                                                                                             |
   +----------------------+-----------+------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | hyperparameters      | No        | JSON Array | Running parameters of a training job. It is a collection of label-value pairs. This parameter is a container environment variable when a job uses a custom image.                                         |
   +----------------------+-----------+------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_url              | No        | String     | OBS URL of the logs of a training job. By default, this parameter is left blank. Example value: **/usr/log/**                                                                                             |
   +----------------------+-----------+------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | train_instance_type  | Yes       | Long       | Resource flavor selected for a training job. If you choose to train on the training platform, obtain the value by calling the API described in :ref:`Obtaining Resource Flavors <modelarts_04_0191>`.     |
   +----------------------+-----------+------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | framework_type       | No        | String     | Engine selected for a training job. Obtain the value by calling the API described in :ref:`Obtaining Engine Types <modelarts_04_0192>`. Leave this parameter blank when **model_name** is set.            |
   +----------------------+-----------+------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | framework_version    | No        | String     | Engine version selected for a training job. Obtain the value by calling the API described in :ref:`Obtaining Engine Types <modelarts_04_0192>`. Leave this parameter blank when **model_name** is set.    |
   +----------------------+-----------+------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | job_description      | No        | String     | Description of a training job                                                                                                                                                                             |
   +----------------------+-----------+------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | user_image_url       | No        | String     | SWR URL of the custom image used by a training job. Example value: **100.125.5.235:20202/jobmng/custom-cpu-base:1.0**                                                                                     |
   +----------------------+-----------+------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | user_command         | No        | String     | Boot command used to start the container of the custom image of a training job. The format is **bash /home/work/run_train.sh python /home/work/user-job-dir/app/train.py {python_file_parameter}**.       |
   +----------------------+-----------+------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** **update_job_configs** request parameters

   +--------------------+-----------+------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter          | Mandatory | Type       | Description                                                                                                                                                                                                                                              |
   +====================+===========+============+==========================================================================================================================================================================================================================================================+
   | config_name        | Yes       | String     | Name of a training job parameter configuration. The value must contain 1 to 20 characters consisting of only digits, letters, underscores (_), and hyphens (-). By default, if this parameter is left blank, the value is dynamically generated by date. |
   +--------------------+-----------+------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | config_desc        | No        | String     | Description of a training job parameter configuration. The value must contain 0 to 256 characters. By default, this parameter is left blank.                                                                                                             |
   +--------------------+-----------+------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | inputs             | No        | String     | OBS storage path of a training job                                                                                                                                                                                                                       |
   +--------------------+-----------+------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dataset_id         | No        | String     | Dataset ID of a training job. This parameter must be used together with **dataset_version_id**, but cannot be used together with **inputs**.                                                                                                             |
   +--------------------+-----------+------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dataset_version_id | No        | String     | Dataset version ID of a training job. This parameter must be used together with **dataset_id**, but cannot be used together with **inputs**.                                                                                                             |
   +--------------------+-----------+------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | data_source        | No        | JSON Array | Dataset of a training job. This parameter cannot be used together with **inputs**, **dataset_id**, or **dataset_version_id**.                                                                                                                            |
   +--------------------+-----------+------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** **data_source** parameters

   +-----------------+-----------+--------+-----------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory | Type   | Description                                                                                         |
   +=================+===========+========+=====================================================================================================+
   | dataset_id      | No        | String | Dataset ID of a training job                                                                        |
   +-----------------+-----------+--------+-----------------------------------------------------------------------------------------------------+
   | dataset_version | No        | String | Dataset version ID of a training job                                                                |
   +-----------------+-----------+--------+-----------------------------------------------------------------------------------------------------+
   | type            | Yes       | String | Dataset type. The value can be **obs** or **dataset**.                                              |
   +-----------------+-----------+--------+-----------------------------------------------------------------------------------------------------+
   | data_url        | No        | String | OBS bucket path. This parameter cannot be used together with **dataset_id** or **dataset_version**. |
   +-----------------+-----------+--------+-----------------------------------------------------------------------------------------------------+

.. table:: **Table 4** **update_job_configs** response parameters

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
