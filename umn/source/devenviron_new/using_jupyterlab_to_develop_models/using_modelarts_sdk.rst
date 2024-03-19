:original_name: modelarts_30_0030.html

.. _modelarts_30_0030:

Using ModelArts SDK
===================

Notebook instances allow you to use ModelArts SDK to manage OBS, training jobs, models, and real-time services.

Your notebook instances have automatically obtained your AK/SK for authentication and the region. Therefore, SDK sessions are automatically authenticated.

Example Code
------------

-  Create a training job.

   ::

      from modelarts.session import Session
      from modelarts.estimator import Estimator
      session = Session()
      estimator = Estimator(
                            modelarts_session=session,
                            framework_type='PyTorch',                                     # AI engine name
                            framework_version='PyTorch-1.0.0-python3.6',                  # AI engine version
                            code_dir='/obs-bucket-name/src/',                             # Training script directory
                            boot_file='/obs-bucket-name/src/pytorch_sentiment.py',        # Training boot script directory
                            log_url='/obs-bucket-name/log/',                              # Training log directory
                            hyperparameters=[
                                             {"label":"classes",
                                              "value": "10"},
                                             {"label":"lr",
                                              "value": "0.001"}
                                             ],
                            output_path='/obs-bucket-name/output/',                         # Training output directory
                            train_instance_type='modelarts.vm.gpu.p100',                  # Training environment specifications
                            train_instance_count=1,                                       # Number of training nodes
                            job_description='pytorch-sentiment with ModelArts SDK')       # Training job description
      job_instance = estimator.fit(inputs='/obs-bucket-name/data/train/', wait=False, job_name='my_training_job')

-  Obtain a model list.

   ::

      from modelarts.session import Session
      from modelarts.model import Model
      session = Session()
      model_list_resp = Model.get_model_list(session, model_status="published", model_name="digit", order="desc")

-  Obtain service details.

   ::

      from modelarts.session import Session
      from modelarts.model import Predictor
      session = Session()
      predictor_instance = Predictor(session, service_id="input your service_id")
      predictor_info_resp = predictor_instance.get_service_info()
