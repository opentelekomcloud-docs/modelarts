:original_name: modelarts_05_3186.html

.. _modelarts_05_3186:

Error Occurred When an API Is Called for Deploying a Model Created Using a Custom Image
=======================================================================================

If an error occurs when an API is called for service deployment, check the following items:

#. Check whether POST is used in the configuration file for the model API.
#. Check whether the URL in the configuration file contains a customized path, for example, **/predictions/poetry** (the default path is **/**).
#. Check whether the called path in the body of the API request contains a customized path, for example, **{API address}/predictions/poetry**.
