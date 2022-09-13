:original_name: modelarts_23_0335.html

.. _modelarts_23_0335:

Using ModelArts SDKs
====================

In notebook instances, you can use ModelArts SDKs to manage OBS, training jobs, models, and real-time services.

For details about how to use ModelArts SDKs, see `ModelArts SDK Reference <https://docs.otc.t-systems.com/en-us/sdkreference/modelarts/modelarts_04_0002.html>`__.

Notebooks carry the authentication (AK/SK) and region information about login users. Therefore, SDK session authentication can be completed without entering parameters.

Example Code
------------

-  Creating a training job

   .. code-block::

      from modelarts.session import Session
      from modelarts.estimator import Estimator
      session = Session()
      estimator = Estimator(
                            modelarts_session=session,
                            framework_type='PyTorch',                                     # AI engine name
                             framework_version='PyTorch-1.0.0-python3.6',                  # AI engine version
                            code_dir='/obs-bucket-name/src/',                                      # Training script directory
                            boot_file='/obs-bucket-name/src/pytorch_sentiment.py',                 # Training startup script directory
                            log_url='/obs-bucket-name/log/',                                       # Training log directory
                            hyperparameters=[
                                             {"label":"classes",
                                              "value": "10"},
                                             {"label":"lr",
                                              "value": "0.001"}
                                             ],
                            output_path='/obs-bucket-name/output/',                                # Training output directory
                            train_instance_type='modelarts.vm.gpu.p100',                  # Training environment specifications
                            train_instance_count=1,                                       # Number of training nodes
                            job_description='pytorch-sentiment with ModelArts SDK')       # Training job description
      job_instance = estimator.fit(inputs='/obs-bucket-name/data/train/', wait=False, job_name='my_training_job')

-  Querying a model list

   .. code-block::

      from modelarts.session import Session
      from modelarts.model import Model
      session = Session()
      model_list_resp = Model.get_model_list(session, model_status="published", model_name="digit", order="desc")

-  Querying service details

   .. code-block::

      from modelarts.session import Session
      from modelarts.model import Predictor
      session = Session()
      predictor_instance = Predictor(session, service_id="input your service_id")
      predictor_info_resp = predictor_instance.get_service_info()
