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

The following error message was displayed.


.. figure:: /_static/images/en-us_image_0000001846138133.png
   :alt: **Figure 1** Error log

   **Figure 1** Error log

Possible Causes
---------------

The possible causes are as follows:

The **NCCL_SOCKET_IFNAME** environment variable that has been set on the cloud is modified to direct to an unavailable NIC. By default, the **NCCL_SOCKET_IFNAME** value set on the cloud is as follows:

.. code-block::

   import os
   os.environ[NCCL_SOCKET_IFNAME]=ib0,bond0,eth0

Solution
--------

#. Correct the **NCCL_SOCKET_IFNAME** setting to comply with the setting on the cloud.
#. Use the local PyCharm to remotely connect to the notebook for debugging.

Summary and Suggestions
-----------------------

Before creating a training job, use the ModelArts development environment to debug the training code to maximally eliminate errors in code migration.
