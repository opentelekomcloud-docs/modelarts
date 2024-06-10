:original_name: modelarts_trouble_0037.html

.. _modelarts_trouble_0037:

Error Message "max_pool2d_with_indices_out_cuda_frame failed with error code 0" Displayed in Logs
=================================================================================================

Symptom
-------

After PyTorch 1.3 was upgraded to 1.4, the following error message was displayed:

.. code-block::

   "RuntimeError:max_pool2d_with_indices_out_cuda_frame failed with error code 0"

Possible Causes
---------------

The possible causes are as follows:

The engine of PyTorch 1.4 is incompatible with that of PyTorch 1.3.

Solution
--------

#. Run the following commands to add contiguous data:

   .. code-block::

      images = images.cuda()
      pred = model(images.permute(0, 3, 1, 2).contigous())

#. Roll back to PyTorch 1.3.

#. Use the local PyCharm to remotely connect to the notebook for debugging.

Summary and Suggestions
-----------------------

Before creating a training job, use the ModelArts development environment to debug the training code to maximally eliminate errors in code migration.
