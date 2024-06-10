:original_name: modelarts_13_0029.html

.. _modelarts_13_0029:

Training Output Path Used by Another Job
========================================

Symptom
-------

The following error message is displayed when a training job is created: Operation failed. Other running job contain train_url: /bucket-20181114/code_hxm/

Possible Cause
--------------

According to the error information, the same training output path is used by another job when a training job is created.

Solution
--------

A training output path can be used by only one job in the running, queuing, or initializing state.

If this error occurs, check and re-set the training output path of the training job to avoid job creation failure.
