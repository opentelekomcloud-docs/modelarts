:original_name: modelarts_13_0033.html

.. _modelarts_13_0033:

No GPU Detected in a Training Job
=================================

Symptom
-------

The following error message is displayed during the running of a ModelArts training job:

.. code-block::

   failed call to cuInit: CUDA_ERROR_NO_DEVICE: no CUDA-capable device is detected

Possible Cause
--------------

According to error information, the error cause is that the training job running program cannot read the GPU.

Solution
--------

Check whether the following configuration information is added to code and set the GPU visible to the program based on the error message:

.. code-block::

   os.environ['CUDA_VISIBLE_DEVICES'] = '0,1,2,3,4,5,6,7'

In the preceding information, **0** is a GPU ID of the server. The GPU ID can be 0, 1, 2, 3, or the like, indicating a GPU ID visible to the program. If the configuration information is not added, the GPU corresponding to the ID is unavailable.
