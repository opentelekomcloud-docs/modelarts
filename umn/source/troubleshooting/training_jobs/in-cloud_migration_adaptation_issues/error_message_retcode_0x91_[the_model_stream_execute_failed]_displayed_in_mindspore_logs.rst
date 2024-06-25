:original_name: modelarts_trouble_0054.html

.. _modelarts_trouble_0054:

Error Message "retCode=0x91, [the model stream execute failed]" Displayed in MindSpore Logs
===========================================================================================

Symptom
-------

When MindSpore is used for training, the following error message is displayed:

.. code-block::

   [ERROR] RUNTIME(3002)model execute error, retCode=0x91, [the model stream execute failed]

Possible Causes
---------------

The speed of reading data cannot keep up with the model iteration speed.

Solution
--------

#. Reduce shuffle operations during preprocessing.

   .. code-block::

      dataset = dataset.shuffle(buffer_size=x)

#. Disable data preprocessing, which may affect system performance.

   .. code-block::

      NPURunConfig(enable_data_pre_proc=Flase)

Summary and Suggestions
-----------------------

Before creating a training job, use the ModelArts development environment to debug the training code to maximally eliminate errors in code migration.
