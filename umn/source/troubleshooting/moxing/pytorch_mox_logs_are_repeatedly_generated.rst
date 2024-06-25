:original_name: modelarts_13_0010.html

.. _modelarts_13_0010:

Pytorch Mox Logs Are Repeatedly Generated
=========================================

Symptom
-------

The Pytorch engine of a frequently-used framework is used as an algorithm source of a ModelArts training job. During the running of the training job, Mox versions for each epoch will be printed in the Pytorch Mox log. The log details are as follows:

.. code-block::

   INFO:root:Using MoXing-v1.13.0-de803ac9
   INFO:root:Using OBS-Python-SDK-3.1.2
   INFO:root:Using MoXing-v1.13.0-de803ac9
   INFO:root:Using OBS-Python-SDK-3.1.2

Possible Cause
--------------

Pytorch creates multiple processes in spawn mode. Each process invokes the Mox to download data in multi-process mode. In this case, subprocesses are destroyed and recreated repeatedly, and Mox is imported repeatedly. As a result, a large amount of Mox version information is printed.

Solution
--------

To avoid repeated output of the Pytorch Mox logs of the training job, you need to add the following code to the boot file. When **MOX_SILENT_MODE = "1"**, Mox version information can be blocked in the log.

.. code-block::

   import os
   os.environ["MOX_SILENT_MODE"] = "1"
