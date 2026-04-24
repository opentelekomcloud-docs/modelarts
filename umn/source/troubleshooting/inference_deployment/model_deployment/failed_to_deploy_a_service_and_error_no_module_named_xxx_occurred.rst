:original_name: modelarts_05_3189.html

.. _modelarts_05_3189:

Failed to Deploy a Service and Error "No Module named XXX" Occurred
===================================================================

Symptom
-------

Deploying a service failed. The system displays error message "No Module named XXX".

Possible Causes
---------------

"No Module named XXX" indicates that the dependency module is not imported to the model.

Solution
--------

Import the required dependency module to the model through inference code.

For example, when you attempt to deploy a PyTorch model as a real-time service, the system displays error message "ModuleNotFoundError: No module named 'model_service.tfserving_model_service'". In this case, configure "from model_service.pytorch_model_service import PTServingBaseService" in **customize_service.py**. Example code:

.. code-block::

   import log
   from model_service.pytorch_model_service import PTServingBaseService
