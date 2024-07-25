:original_name: modelarts_13_0030.html

.. _modelarts_13_0030:

Training Job Status Is Reviewing Job Initialization
===================================================

Symptom
-------

When **Algorithm Source** is set to **Custom** during training job creation, the training job status is **Reviewing Job Initialization**.

Possible Cause
--------------

When a custom image is running for the first time, the image needs to be reviewed first. After the image is reviewed, you can create a job. That is, the current status is **Reviewing Job Initialization**.
