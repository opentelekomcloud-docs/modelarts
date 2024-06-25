:original_name: modelarts_05_0080.html

.. _modelarts_05_0080:

Do Files in /cache Still Exist After a Notebook Instance is Stopped or Restarted? How Do I Avoid a Restart?
===========================================================================================================

Temporary files are stored in the **/cache** directory and will not be saved after the notebook instance is stopped or restarted. Data stored in the **/home/ma-user/work** directory will be retained after the notebook instance is stopped or restarted.

To avoid a restart, do not train heavy-load jobs that consume large amounts of CPU, GPU, or memory resources in the development environment.
