.. _modelarts_23_0335:

Using ModelArts SDKs
====================

In notebook instances, you can use ModelArts SDKs to manage OBS, training jobs, models, and real-time services.

For details about how to use ModelArts SDKs, see *ModelArts SDK Reference*.

Notebooks carry the authentication (AK/SK) and region information about login users. Therefore, SDK session authentication can be completed without entering parameters.

Example Code
------------

-  Creating a training job

   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | ::                                | ::                                                                                                                                  |
   |                                   |                                                                                                                                     |
   |     1                             |    from modelarts.session import Session                                                                                            |
   |     2                             |    from modelarts.estimator import Estimator                                                                                        |
   |     3                             |    session = Session()                                                                                                              |
   |     4                             |    estimator = Estimator(                                                                                                           |
   |     5                             |                          modelarts_session=session,                                                                                 |
   |     6                             |                          framework_type='PyTorch',                                     # AI engine name                             |
   |     7                             |                           framework_version='PyTorch-1.0.0-python3.6',                  # AI engine version                         |
   |     8                             |                          code_dir='/obs-bucket-name/src/',                                      # Training script directory         |
   |     9                             |                          boot_file='/obs-bucket-name/src/pytorch_sentiment.py',                 # Training startup script directory |
   |    10                             |                          log_url='/obs-bucket-name/log/',                                       # Training log directory            |
   |    11                             |                          hyperparameters=[                                                                                          |
   |    12                             |                                           {"label":"classes",                                                                       |
   |    13                             |                                            "value": "10"},                                                                          |
   |    14                             |                                           {"label":"lr",                                                                            |
   |    15                             |                                            "value": "0.001"}                                                                        |
   |    16                             |                                           ],                                                                                        |
   |    17                             |                          output_path='/obs-bucket-name/output/',                                # Training output directory         |
   |    18                             |                          train_instance_type='modelarts.vm.gpu.p100',                  # Training environment specifications        |
   |    19                             |                          train_instance_count=1,                                       # Number of training nodes                   |
   |    20                             |                          job_description='pytorch-sentiment with ModelArts SDK')       # Training job description                   |
   |    21                             |    job_instance = estimator.fit(inputs='/obs-bucket-name/data/train/', wait=False, job_name='my_training_job')                      |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+

-  Querying a model list

   +-----------------------------------+----------------------------------------------------------------------------------------------------------------+
   | ::                                | ::                                                                                                             |
   |                                   |                                                                                                                |
   |    1                              |    from modelarts.session import Session                                                                       |
   |    2                              |    from modelarts.model import Model                                                                           |
   |    3                              |    session = Session()                                                                                         |
   |    4                              |    model_list_resp = Model.get_model_list(session, model_status="published", model_name="digit", order="desc") |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------+

-  Querying service details

   +-----------------------------------+--------------------------------------------------------------------------------+
   | ::                                | ::                                                                             |
   |                                   |                                                                                |
   |    1                              |    from modelarts.session import Session                                       |
   |    2                              |    from modelarts.model import Predictor                                       |
   |    3                              |    session = Session()                                                         |
   |    4                              |    predictor_instance = Predictor(session, service_id="input your service_id") |
   |    5                              |    predictor_info_resp = predictor_instance.get_service_info()                 |
   +-----------------------------------+--------------------------------------------------------------------------------+
