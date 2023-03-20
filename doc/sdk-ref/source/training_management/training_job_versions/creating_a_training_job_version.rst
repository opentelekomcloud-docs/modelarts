:original_name: modelarts_04_0168.html

.. _modelarts_04_0168:

Creating a Training Job Version
===============================

A training job must exist before you create a version for it. You can create a training job version based on :ref:`Creating a Training Job <modelarts_04_0131>` or **job_id** and **version_id** of the object returned by :ref:`Querying the List of Training Job Versions <modelarts_04_0169>`.

Sample Code
-----------

In the ModelArts notebook instance, you do not need to enter authentication parameters for session authentication. For details about session authentication of other development environments, see :ref:`Session Authentication <modelarts_04_0123>`.

-  Example 1: Create a training job version using the data stored on OBS.

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
                            output_path='/bucket/output/',                                # Training output directory
                            train_instance_type='modelarts.vm.gpu.p100',                  # Training environment flavor
                            train_instance_count=1)
      job_version_instance = estimator.create_job_version(job_id='182626', pre_version_id=278813, inputs='/bucket/data/train/', wait=False, job_desc='create a job version')

-  Example 2: Create a training job version using a dataset.

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
                            output_path='/bucket/output/',                                # Training output directory
                            train_instance_type='modelarts.vm.gpu.p100',                  # Training environment flavor
                            train_instance_count=1,                                       # Number of training nodes
                            job_description='pytorch-sentiment with ModelArts SDK')       # Training job description
      job_version_instance = estimator.create_job_version(job_id='182626', pre_version_id=278813, inputs='/bucket/data/train/', wait=False, job_desc='create a job version')

-  Example 3: Create a training job version using a custom image.

   ::

      from modelarts.session import Session
      from modelarts.estimator import Estimator
      session = Session()
      estimator = Estimator(
                            modelarts_session=session,
                            log_url='/bucket/log/',                                       # Training log directory
                            hyperparameters=[
                                             {"label":"classes",
                                              "value": "10"},
                                             {"label":"lr",
                                              "value": "0.001"}
                                             ],
                            output_path='/bucket/output/',                                # Training output directory
                            train_instance_type='modelarts.vm.gpu.p100',                  # Training environment flavor
                            train_instance_count=1,                                       # Number of training nodes
                            user_command='bash -x /home/work/run_train.sh python /home/work/user-job-dir/app/mnist/mnist_softmax.py --data_url /home/work/user-job-dir/app/mnist_data',                                                            # Boot command of the custom image
                            user_image_url='100.125.5.235:20202/jobmng/cpu-base:1.0',     # Address for downloading the custom image
                            job_description='pytorch-sentiment with ModelArts SDK')       # Training job description
      job_version_instance = estimator.create_job_version(job_id='182626', pre_version_id=278813, inputs='/bucket/data/train/', wait=False, job_desc='create a job version')

Parameter Description
---------------------

.. table:: **Table 1** Estimator request parameters

   +----------------------+-----------+------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter            | Mandatory | Type       | Description                                                                                                                                                                                                       |
   +======================+===========+============+===================================================================================================================================================================================================================+
   | modelarts_session    | Yes       | Object     | Session object. For details about the initialization method, see :ref:`Session Authentication <modelarts_04_0123>`.                                                                                               |
   +----------------------+-----------+------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | train_instance_count | Yes       | Long       | Number of workers in a training job                                                                                                                                                                               |
   +----------------------+-----------+------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | code_dir             | No        | String     | Code directory of a training job, for example, **/bucket/src/**. Leave this parameter blank when **model_name** is set.                                                                                           |
   +----------------------+-----------+------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | boot_file            | No        | String     | Boot file of a training job, which needs to be stored in the code directory. For example, **/bucket/src/boot.py**. Leave this parameter blank when **model_name** is set.                                         |
   +----------------------+-----------+------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | output_path          | Yes       | String     | Output path of a training job                                                                                                                                                                                     |
   +----------------------+-----------+------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | hyperparameters      | No        | JSON Array | Running parameters of a training job. It is a collection of label-value pairs of the string type. This parameter is a container environment variable when a job uses a custom image.                              |
   +----------------------+-----------+------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_url              | No        | String     | OBS URL of the logs of a training job. By default, this parameter is left blank. Example value: **/usr/log/**                                                                                                     |
   +----------------------+-----------+------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | train_instance_type  | Yes       | Long       | Resource flavor selected for a training job. If you choose to train on the training platform, obtain the value by calling the API described in :ref:`Querying the List of Resource Flavors <modelarts_04_0191>`.  |
   +----------------------+-----------+------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | framework_type       | No        | String     | Engine selected for a training job. Obtain the value by calling the API described in :ref:`Querying the List of Engine Types <modelarts_04_0192>`. Leave this parameter blank when **model_name** is set.         |
   +----------------------+-----------+------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | framework_version    | No        | String     | Engine version selected for a training job. Obtain the value by calling the API described in :ref:`Querying the List of Engine Types <modelarts_04_0192>`. Leave this parameter blank when **model_name** is set. |
   +----------------------+-----------+------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | user_image_url       | No        | String     | SWR URL of the custom image used by a training job. Example value: **100.125.5.235:20202/jobmng/custom-cpu-base:1.0**                                                                                             |
   +----------------------+-----------+------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | user_command         | No        | String     | Boot command used to start the container of the custom image of a training job. The format is **bash /home/work/run_train.sh python /home/work/user-job-dir/app/train.py {python_file_parameter}**.               |
   +----------------------+-----------+------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** **create_job_version** request parameters

   +--------------------+-----------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter          | Mandatory | Type    | Description                                                                                                                                                                                                                                                                                                                |
   +====================+===========+=========+============================================================================================================================================================================================================================================================================================================================+
   | job_id             | Yes       | String  | ID of a training job. You can query **job_id** using the training job object generated in :ref:`Creating a Training Job <modelarts_04_0131>`, for example, **job_instance.job_id**, or from the response obtained in :ref:`Obtaining Training Jobs <modelarts_04_0160>`.                                                   |
   +--------------------+-----------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | pre_version_id     | Yes       | Long    | ID of the previous version of a training job. You can query **pre_version_id** using the training job object generated in :ref:`Creating a Training Job <modelarts_04_0131>`, for example, **job_instance.version_id**, or from the response obtained in :ref:`Obtaining Training Jobs <modelarts_04_0160>`.               |
   +--------------------+-----------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | inputs             | Yes       | String  | Data storage location of a training job. **inputs** cannot be used with **dataset_id** and **dataset_version_id**, or with **data_source** at the same time. However, one of the parameters must exist. Only this parameter is supported in local training.                                                                |
   +--------------------+-----------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dataset_id         | No        | String  | Dataset ID of a training job. This parameter must be used together with **dataset_version_id**, but cannot be used together with **inputs**. To obtain the dataset ID, `view basic information about the dataset <https://docs.otc.t-systems.com/modelarts/umn/data_management/managing_dataset_versions.html>`__.         |
   +--------------------+-----------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dataset_version_id | No        | String  | Dataset version ID of a training job. This parameter must be used together with **dataset_id**, but cannot be used together with **inputs**. To obtain the dataset version ID, `view basic information about the dataset <https://docs.otc.t-systems.com/modelarts/umn/data_management/managing_dataset_versions.html>`__. |
   +--------------------+-----------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | wait               | No        | Boolean | Whether to wait for the completion of creating a training job version. Default value: **False**                                                                                                                                                                                                                            |
   +--------------------+-----------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | job_desc           | No        | String  | Description of a training job                                                                                                                                                                                                                                                                                              |
   +--------------------+-----------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** **create_job_version** response parameters

   +-------------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Type   | Description                                                                                                                                                                                                                                                                       |
   +=============+========+===================================================================================================================================================================================================================================================================================+
   | TrainingJob | Object | Training object. This object contains attributes such as **job_id** and **version_id**, and operations on a training job, such as querying, modifying, or deleting the training job. For example, you can use **job_version_instance.job_id** to obtain the ID of a training job. |
   +-------------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
