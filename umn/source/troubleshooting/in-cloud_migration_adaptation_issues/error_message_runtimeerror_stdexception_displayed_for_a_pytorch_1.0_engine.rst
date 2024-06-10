:original_name: modelarts_trouble_0036.html

.. _modelarts_trouble_0036:

Error Message "RuntimeError: std::exception" Displayed for a PyTorch 1.0 Engine
===============================================================================

Symptom
-------

When a PyTorch 1.0 image is used, the following error message is displayed:

.. code-block::

   "RuntimeError: std::exception"

Possible Causes
---------------

The possible causes are as follows:

The soft link of libmkldnn in the PyTorch 1.0 image conflicts with that of the native Torch. For details, see `conv1d fails in PyTorch 1.0 <https://github.com/pytorch/pytorch/issues/14952>`__.

Solution
--------

#. This issue is caused by library conflict in the environment. To resolve this issue, add the following code at the very beginning of the boot script:

   .. code-block::

      import os
      os.system("rm /home/work/anaconda3/lib/libmkldnn.so")
      os.system("rm /home/work/anaconda3/lib/libmkldnn.so.0")

#. Use the local PyCharm to remotely connect to the notebook for debugging.

Summary and Suggestions
-----------------------

Before creating a training job, use the ModelArts development environment to debug the training code to maximally eliminate errors in code migration.
