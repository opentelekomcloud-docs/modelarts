.. _modelarts_05_0080:

Do Files in /cache Still Exist After a Notebook Instance is Stopped or Restarted? How Do I Avoid a Restart?
===========================================================================================================

**/cache** is a temporary directory and will not be saved. After an instance using OBS storage is stopped, data in the **~work** directory will be deleted. After a notebook instance is restarted, all cached data except the data in the OBS bucket is lost, and your model or code is unavailable.

To avoid a restart, do not train heavy-load jobs that consume large amounts of CPU, GPU, or memory resources in DevEnviron.
