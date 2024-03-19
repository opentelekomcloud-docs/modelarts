:original_name: modelarts_trouble_0047.html

.. _modelarts_trouble_0047:

Reinstalled CUDA Version Does Not Match the One in the Target Image
===================================================================

Symptom
-------

An error occurred after the engine version was reinstalled or a new CUDA package was compiled based on the existing image.

.. code-block::

   1. "RuntimeError: cuda runtime error (11) : invalid argument at /pytorch/aten/src/THC/THCCachingHostAllocator.cpp:278"
   2. "libcudart.so.9.0 cannot open shared object file no such file or directory"
   3. "Make sure the device specification refers to a valid device. The requested device appears to be a GPU,but CUDA is not enabled"

Possible Causes
---------------

The possible causes are as follows:

The CUDA version of the newly installed package does not match the CUDA version in the image.

Solution
--------

Use the local PyCharm to remotely connect to the notebook for debugging and installation.

#. Remotely log in to the selected image and run **nvcc -V** to obtain the CUDA version of the image.
#. Reinstall the Torch. Ensure that the version matches the one obtained in the previous step.

Summary and Suggestions
-----------------------

Before creating a training job, use the ModelArts development environment to debug the training code to maximally eliminate errors in code migration.
