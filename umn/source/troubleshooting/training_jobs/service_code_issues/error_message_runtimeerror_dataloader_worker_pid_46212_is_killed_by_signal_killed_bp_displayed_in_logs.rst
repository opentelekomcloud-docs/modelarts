:original_name: modelarts_trouble_0060.html

.. _modelarts_trouble_0060:

Error Message "Runtimeerror: Dataloader worker (pid 46212) is killed by signal: Killed BP" Displayed in Logs
============================================================================================================

Symptom
-------

During the running of a training job, error message "Runtimeerror: Dataloader worker (pid 46212) is killed by signal: Killed BP" is displayed in logs.

Possible Causes
---------------

The Dataloader process exits because the batch size is too large.

Solution
--------

Decrease the batch size.
