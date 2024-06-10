:original_name: modelarts_trouble_0034.html

.. _modelarts_trouble_0034:

Error Message "Network is unreachable" Displayed in Logs
========================================================

Symptom
-------

When PyTorch is used, the following error message is displayed in logs after **pretrained** in **torchvision.models** is set to **True**:

.. code-block::

   'OSError: [Errno 101] Network is unreachable'

Possible Causes
---------------

The possible causes are as follows:

For security purposes, ModelArts internal training machines are not allowed to access the Internet.

Solution
--------

#. Change the **pretrained** value to **False**, download the pre-trained model, and load the path to this model.

   .. code-block::

      import torch
      import torchvision.models as models

      model1 = models.resnet34(pretrained=False, progress=True)
      checkpoint = '/xxx/resnet34-333f7ec4.pth'
      state_dict = torch.load(checkpoint)
      model1.load_state_dict(state_dict)

#. Use the local PyCharm to remotely connect to the notebook for debugging.

Summary and Suggestions
-----------------------

Before creating a training job, use the ModelArts development environment to debug the training code to maximally eliminate errors in code migration.
