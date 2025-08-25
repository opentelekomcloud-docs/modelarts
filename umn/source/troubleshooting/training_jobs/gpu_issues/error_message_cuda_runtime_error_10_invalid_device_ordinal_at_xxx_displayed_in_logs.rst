:original_name: modelarts_trouble_0049.html

.. _modelarts_trouble_0049:

Error Message "cuda runtime error (10) : invalid device ordinal at xxx" Displayed in Logs
=========================================================================================

Symptom
-------

A training job failed, and the following error is displayed in logs.


.. figure:: /_static/images/en-us_image_0000002340888720.png
   :alt: **Figure 1** Error log

   **Figure 1** Error log

Possible Causes
---------------

The possible causes are as follows:

-  The **CUDA_VISIBLE_DEVICES** setting does not comply with job specifications. For example, you select a job with four GPUs, and the IDs of available GPUs are 0, 1, 2, and 3. However, when you perform CUDA operations, for example **tensor.to(device="cuda:7")**, tensors are specified to run on GPU 7, which is beyond the available GPU IDs.
-  GPUs are damaged on resource nodes if CUDA operations are performed on a GPU with a specified ID. As a result, the number of GPUs that can be detected is less than the selected specifications.

Solution
--------

#. Perform CUDA operations on the GPUs with IDs specified by **CUDA_VISIBLE_DEVICES**.
#. If a GPU on a resource node is damaged, contact technical support.

Summary and Suggestions
-----------------------

Before creating a training job, use the ModelArts development environment to debug the training code to maximally eliminate errors in code migration.
