:original_name: modelarts_13_0037.html

.. _modelarts_13_0037:

Copying Data Using MoXing Is Slow and the Log Is Repeatedly Printed in a Training Job
=====================================================================================

Symptom
-------

-  Copying data using MoXing is slow in a ModelArts training job.

-  The log **INFO:root:Listing OBS** is repeatedly printed.


   .. figure:: /_static/images/en-us_image_0000001943968397.png
      :alt: **Figure 1** Repeated log printing

      **Figure 1** Repeated log printing

Possible Cause
--------------

#. The possible causes for slow data copying are as follows:

   -  Reading data from OBS will make data reading become a training bottleneck, resulting in slow iteration.
   -  Data fails to be read from OBS due to environment or network issues. As a result, the job fails.

#. The log is printed repeatedly. The log indicates that the file is being read from the remote end. After the file list is read, data starts to be downloaded. If there are many files, this process takes a long time.

Solution
--------

When creating a training job, you can save data to OBS. You are advised not to use the OBS APIs of TensorFlow, MXNet, and PyTorch to directly read data from OBS.

-  If the file is small, you can save data on OBS as a **.tar** package. When starting the training, download the package from OBS to the **/cache** directory and decompress the package.

-  If the file is large, save data as multiple **.tar** packages and invoke multiple processes in the entry script to decompress data in parallel. You are advised not to save discrete files to OBS. Otherwise, data download will be slow.

-  In a training job, use the following code to decompress the **.tar** package:

   .. code-block::

      import moxing as mox
      import os
      mox.file.copy_parallel("obs://donotdel-modelarts-test/AI/data/PyTorch-1.0.1/tiny-imagenet-200.tar", '/cache/tiny-imagenet-200.tar')
      os.system('cd /cache; tar -xvf tiny-imagenet-200.tar > /dev/null 2>&1')
