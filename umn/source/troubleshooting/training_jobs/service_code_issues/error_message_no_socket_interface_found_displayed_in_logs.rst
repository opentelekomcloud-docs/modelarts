:original_name: modelarts_trouble_0038.html

.. _modelarts_trouble_0038:

Error Message "no socket interface found" Displayed in Logs
===========================================================

Symptom
-------

An NCCL debug log level is set in a distributed job executed using a PyTorch image.

.. code-block::

   import os
   os.environ["NCCL_DEBUG"] = "INFO"

The following error message is displayed.


.. figure:: /_static/images/en-us_image_0000002374727229.png
   :alt: **Figure 1** Error log

   **Figure 1** Error log

Possible Causes
---------------

The environment variables **NCCL_IB_TC**, **NCCL_IB_GID_INDEX**, and **NCCL_IB_TIMEOUT** are not configured. As a result, the communication is slow and unstable, and the IB communication is interrupted.

Solution
--------

Add environment variables to the code.

.. code-block::

   import os
   os.environ["NCCL_IB_TC"] = "128"
   os.environ["NCCL_IB_GID_INDEX"] = "3"
   os.environ["NCCL_IB_TIMEOUT"] = "22"
