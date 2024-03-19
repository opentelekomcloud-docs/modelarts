:original_name: modelarts_trouble_0032.html

.. _modelarts_trouble_0032:

Error Message "No CUDA-capable device is detected" Displayed in Logs
====================================================================

Symptom
-------

An error similar to the following occurs during the running of the program:

.. code-block::

   1. 'failed call to cuInit: CUDA_ERROR_NO_DEVICE:  no CUDA-capable device is detected'
   2. 'No CUDA-capable device is detected although requirements are installed'

Possible Causes
---------------

The possible causes are as follows:

-  **CUDA_VISIBLE_DEVICES** has been incorrectly set.
-  CUDA operations are performed on GPUs with IDs that are not specified by **CUDA_VISIBLE_DEVICES**.

Solution
--------

#. Do not change the **CUDA_VISIBLE_DEVICES** value in the code. Use its default value.

#. Ensure that the specified GPU IDs are within the available GPU IDs.

#. If the error persists, print the **CUDA_VISIBLE_DEVICES** value and debug it in the notebook, or run the following commands to check whether the returned result is **True**:

   .. code-block::

      import torch
      torch.cuda.is_available()

Summary and Suggestions
-----------------------

Before creating a training job, use the ModelArts development environment to debug the training code to maximally eliminate errors in code migration.
