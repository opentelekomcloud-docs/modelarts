:original_name: modelarts_trouble_0044.html

.. _modelarts_trouble_0044:

Training Job Failed Due to OOM
==============================

Symptom
-------

If a training job failed due to out of memory (OOM), possible symptoms were as follows:

#. Error code 137 is returned.

#. The log file contained error information with keyword **killed**.


   .. figure:: /_static/images/en-us_image_0000001799498528.png
      :alt: **Figure 1** Error log

      **Figure 1** Error log

#. Error message "RuntimeError: CUDA out of memory." was printed in logs.


   .. figure:: /_static/images/en-us_image_0000001846057625.png
      :alt: **Figure 2** Error log

      **Figure 2** Error log

#. Error message "Dst tensor is not initialized" was printed in TensorFlow logs.

Possible Causes
---------------

The possible causes are as follows:

-  GPU memory is insufficient.
-  OOM occurred on certain nodes. This issue is typically caused by the node fault.

Solution
--------

#. Modify hyperparameter settings to release unnecessary tensors.

   a. Modify network parameters, such as **batch_size**, **hide_layer**, and **cell_nums**.

   b. Release unnecessary tensors.

      .. code-block::

         del tmp_tensor
         torch.cuda.empty_cache()

#. Use the local PyCharm to remotely connect to the notebook for debugging.
#. If the fault persists, submit a service ticket to locate the fault or even isolate the affected node.

Summary and Suggestions
-----------------------

Before creating a training job, use the ModelArts development environment to debug the training code to maximally eliminate errors in code migration.
