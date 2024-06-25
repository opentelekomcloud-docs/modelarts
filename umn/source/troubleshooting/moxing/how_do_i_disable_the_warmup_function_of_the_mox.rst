:original_name: modelarts_13_0024.html

.. _modelarts_13_0024:

How Do I Disable the Warmup Function of the Mox?
================================================

Symptom
-------

When the TensorFlow version of the training job Mox is running, 50 steps are executed for four times before the job is formally running.

Warmup indicates a process of using a small learning rate to train several epochs first. Network parameters are randomly initialized. If a large learning rate is used at the beginning, the value may be unstable. This is why warmup is used. After the training process is basically stable, the originally set initial learning rate can be used for training.

Possible Cause
--------------

There are multiple execution modes for distributed TensorFlow. Mox executes 50 steps for four times to record the execution time, and selects the model with the minimum execution time.

Solution
--------

When creating a training job, add **variable_update=parameter_server** in **Running Parameter** to disable the warmup function of Mox.
