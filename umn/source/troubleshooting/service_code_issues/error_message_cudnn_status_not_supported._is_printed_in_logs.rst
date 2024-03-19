:original_name: modelarts_trouble_0056.html

.. _modelarts_trouble_0056:

Error Message "CUDNN_STATUS_NOT_SUPPORTED." Is Printed in Logs
==============================================================

Symptom
-------

The following error message was displayed during PyTorch training:

.. code-block::

   RuntimeError: cuDNN error: CUDNN_STATUS_NOT_SUPPORTED. This error may appear if you passed in a non-contiguous input.

Possible Causes
---------------

The possible causes are as follows:

The data input is not of the contiguous type and is not supported by cuDNN.

Solution
--------

#. Disable cuDNN before training.

   .. code-block::

      torch.backends.cudnn.enabled = False

#. Convert the input data into contiguous data.

   .. code-block::

      images = images.cuda()
      images = images.permute(0, 3, 1, 2).contigous()

Summary and Suggestions
-----------------------

Before creating a training job, use the ModelArts development environment to debug the training code to maximally eliminate errors in code migration.
