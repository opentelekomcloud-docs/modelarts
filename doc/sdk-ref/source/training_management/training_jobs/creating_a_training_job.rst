:original_name: modelarts_04_0131.html

.. _modelarts_04_0131:

Creating a Training Job
=======================

If a training job failed on the training platform, view detailed logs on the platform or by calling the API in :ref:`Obtaining Training Job Logs <modelarts_04_0164>`.

Sample Code
-----------

In ModelArts notebook, you do not need to enter authentication parameters for session authentication. For details about session authentication of other development environments, see :ref:`Session Authentication <modelarts_04_0123>`.

-  Example 1: Create a training job using the data stored on OBS.

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
                            train_instance_type='modelarts.vm.cpu.2u',                  # Training environment flavor
                            train_instance_count=1,                                       # Number of training nodes
                            job_description='pytorch-sentiment with ModelArts SDK')       # Training job description
      job_instance = estimator.fit(inputs='/bucket/data/train/', wait=False, job_name='my_training_job')

-  Example 2: Create a training job using a dataset.

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
                            train_instance_type='modelarts.vm.cpu.2u',                  # Training environment flavor
                            train_instance_count=1,                                       # Number of training nodes
                            job_description='pytorch-sentiment with ModelArts SDK')       # Training job description
      job_instance = estimator.fit(dataset_id='your_dataset_id', dataset_version_id='your_dataset_version_id', wait=False, job_name='my_training_job')

-  Example 3: Create a training job using a custom image.

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
                            train_instance_type='modelarts.vm.cpu.2u',                  # Training environment flavor
                            train_instance_count=1,                                       # Number of training nodes
                            user_command='bash -x /home/work/run_train.sh python /home/work/user-job-dir/app/mnist/mnist_softmax.py --data_url /home/work/user-job-dir/app/mnist_data',                                                            # Boot command of the custom image
                            user_image_url='100.125.5.235:20202/jobmng/cpu-base:1.0',     # Address for downloading the custom image
                            job_description='pytorch-sentiment with ModelArts SDK')       # Training job description
      job_instance = estimator.fit(inputs='/bucket/data/train/', wait=False, job_name='my_training_job')

Parameter Description
---------------------

.. table:: **Table 1** Estimator request parameters

   +----------------------+-----------+------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter            | Mandatory | Type       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   +======================+===========+============+================================================================================================================================================================================================================================================================================================================================================================================================================================================================+
   | modelarts_session    | Yes       | Object     | Session object. For details about the initialization method, see :ref:`Session Authentication <modelarts_04_0123>`.                                                                                                                                                                                                                                                                                                                                            |
   +----------------------+-----------+------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | train_instance_count | Yes       | Long       | Number of compute nodes in a training job                                                                                                                                                                                                                                                                                                                                                                                                                      |
   +----------------------+-----------+------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | code_dir             | No        | String     | Code directory of a training job, for example, **/bucket/src/**. Leave this parameter blank when **model_name** is set.                                                                                                                                                                                                                                                                                                                                        |
   +----------------------+-----------+------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | boot_file            | No        | String     | Boot file of a training job, which needs to be stored in the code directory. For example, **/bucket/src/boot.py**. Leave this parameter blank when **model_name** is set.                                                                                                                                                                                                                                                                                      |
   +----------------------+-----------+------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | output_path          | Yes       | String     | Output path of a training job                                                                                                                                                                                                                                                                                                                                                                                                                                  |
   +----------------------+-----------+------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | hyperparameters      | No        | JSON Array | Running parameters of a training job. It is a collection of label-value pairs of the string type. This parameter is a container environment variable when a job uses a custom image. For details about hyperparameters if a built-in algorithm is used, see `Algorithms and Their Running Parameters <https://docs.otc.t-systems.com/modelarts/umn/training_management/built-in_algorithms/algorithms_and_their_running_parameters.html#modelarts-23-0158>`__. |
   +----------------------+-----------+------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_url              | No        | String     | OBS URL of the logs of a training job. By default, this parameter is left blank. Example value: **/usr/log/**                                                                                                                                                                                                                                                                                                                                                  |
   +----------------------+-----------+------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | train_instance_type  | Yes       | Long       | Resource flavor selected for a training job. If you choose to train on the training platform, obtain the value by calling the API described in :ref:`Obtaining Resource Flavors <modelarts_04_0191>`.                                                                                                                                                                                                                                                          |
   +----------------------+-----------+------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | framework_type       | No        | String     | Engine selected for a training job. Obtain the value by calling the API described in :ref:`Obtaining Engine Types <modelarts_04_0192>`. Leave this parameter blank when **model_name** is set.                                                                                                                                                                                                                                                                 |
   +----------------------+-----------+------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | framework_version    | No        | String     | Engine version selected for a training job. Obtain the value by calling the API described in :ref:`Obtaining Engine Types <modelarts_04_0192>`. Leave this parameter blank when **model_name** is set.                                                                                                                                                                                                                                                         |
   +----------------------+-----------+------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | job_description      | No        | String     | Description of a training job                                                                                                                                                                                                                                                                                                                                                                                                                                  |
   +----------------------+-----------+------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | user_image_url       | No        | String     | SWR URL of the custom image used by a training job. Example value: **100.125.5.235:20202/jobmng/custom-cpu-base:1.0**                                                                                                                                                                                                                                                                                                                                          |
   +----------------------+-----------+------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | user_command         | No        | String     | Boot command used to start the container of the custom image of a training job. The format is **bash /home/work/run_train.sh python /home/work/user-job-dir/app/train.py {python_file_parameter}**.                                                                                                                                                                                                                                                            |
   +----------------------+-----------+------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** **fit** request parameters

   +--------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter          | Mandatory       | Type            | Description                                                                                                                                                                                              |
   +====================+=================+=================+==========================================================================================================================================================================================================+
   | inputs             | Yes             | String          | Data storage location of a training job.                                                                                                                                                                 |
   |                    |                 |                 |                                                                                                                                                                                                          |
   |                    |                 |                 | **inputs** cannot be used with **dataset_id** and **dataset_version_id**, or with **data_source** at the same time. However, one of the parameters must exist.                                           |
   |                    |                 |                 |                                                                                                                                                                                                          |
   |                    |                 |                 | Only this parameter is supported in local training.                                                                                                                                                      |
   +--------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dataset_id         | No              | String          | Dataset ID of a training job. To obtain the dataset ID, `view basic information about the dataset <https://docs.otc.t-systems.com/en-us/usermanual/modelarts/modelarts_23_0019.html>`__.                 |
   |                    |                 |                 |                                                                                                                                                                                                          |
   |                    |                 |                 | This parameter must be used together with **dataset_version_id**, but cannot be used together with **inputs**.                                                                                           |
   +--------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dataset_version_id | No              | String          | Dataset version ID of a training job. To obtain the dataset version ID, `view basic information about the dataset <https://docs.otc.t-systems.com/en-us/usermanual/modelarts/modelarts_23_0019.html>`__. |
   |                    |                 |                 |                                                                                                                                                                                                          |
   |                    |                 |                 | This parameter must be used together with **dataset_id**, but cannot be used together with **inputs**.                                                                                                   |
   +--------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | wait               | No              | Boolean         | Whether to wait for the completion of a training job. Default value: **False**                                                                                                                           |
   +--------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | job_name           | No              | String          | Name of a training job, consisting of 1 to 64 alphanumeric characters. If this parameter is left blank, a job name is generated randomly.                                                                |
   +--------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Parameters in the successful response to training

   +-------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Type   | Description                                                                                                                                                                                                                                                               |
   +=============+========+===========================================================================================================================================================================================================================================================================+
   | TrainingJob | Object | Training object. This object contains attributes such as **job_id** and **version_id**, and operations on a training job, such as querying, modifying, or deleting the training job. For example, you can use **job_instance.job_id** to obtain the ID of a training job. |
   +-------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
