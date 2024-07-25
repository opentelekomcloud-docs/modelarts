:original_name: modelarts_05_0167.html

.. _modelarts_05_0167:

What Do I Do If cudaCheckError Occurs During Training?
======================================================

Symptom
-------

The following error occurs when the training code is executed in a notebook:

.. code-block::

   cudaCheckError() failed : no kernel image is available for execution on the device

Possible Cause
--------------

Parameters **arch** and **code** in **setup.py** have not been set to match the GPU compute power.

Solution
--------

For Tesla V100 GPUs, the GPU compute power is **-gencode arch=compute_70,code=[sm_70,compute_70]**. Set the compilation parameters in **setup.py** accordingly.
