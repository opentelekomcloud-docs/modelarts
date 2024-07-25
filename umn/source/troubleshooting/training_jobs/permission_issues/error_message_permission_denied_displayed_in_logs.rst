:original_name: modelarts_trouble_0046.html

.. _modelarts_trouble_0046:

Error Message "Permission denied" Displayed in Logs
===================================================

Symptom
-------

When a training job accesses the attached EFS disks or executes the .sh boot script, an error occurs.

-  [Errno 13]Permission denied: '/xxx/xxxx'


   .. figure:: /_static/images/en-us_image_0000001943968053.png
      :alt: **Figure 1** Error log

      **Figure 1** Error log

-  bash: /bin/ln: Permission denied

-  bash:/home/ma-user/.pip/pip.conf: Permission Denied (in a custom image)

-  tee: /xxx/xxxx: Permission denied cp: cannot stat '' No such file or directory (in a custom image)

Possible Causes
---------------

The possible causes are as follows:

-  [Errno 13]Permission denied: '/xxx/xxxx'

   -  When data is uploaded, the ownership and permissions to the file are not changed. As a result, the work user group does not have the permission to access the training job.
   -  After the .sh file in the code directory is copied to the container, the execution permission is not granted for the file.

-  bash: /bin/ln: Permission denied

   For security purposes, the ln command is not supported.

-  bash:/home/ma-user/.pip/pip.conf: Permission Denied

   After the version of training jobs is switched from V1 to V2, the UID of the **ma-user** user is still **1102**.

-  tee: /xxx/xxxx: Permission denied cp: cannot stat '': No such file or directory

   The used startup script is **run_train.sh** of an earlier version. Some environment variables in the script are unavailable in the training jobs of the new version.

-  The APIs using the Python file concurrently read and write the same file.

Solution
--------

#. Add permissions to access the attached EFS disks so that the permissions are the same as those of user group (1000) used in the training container. For example, if the **/nas** disk is attached, run the following command:

   .. code-block::

      chown -R 1000: 1000 /nas
      Or
      chmod 777 -R /nas

#. If the execution permission has not been granted for the .sh file used by the custom image, run **chmod +x xxx.sh** to grant the permission before starting the script.

#. On the ModelArts management console, if a training job is created using a custom image, a V2 container image is started using UID 1000 by default. In this case, change the UID of the **ma-user** user from 1102 to 1000. To obtain the sudo permission, comment out the sudoers line.

   |image1|

#. Migrate environment variables from V1 training jobs to V2 training jobs.

   -  Use V2 **MA_NUM_HOSTS** (the number of selected training nodes) to replace V1 **DLS_TASK_NUMBER**.
   -  Use V2 **VC_TASK_INDEX** (or **MA_TASK_INDEX** that will be available later) to replace V1 **DLS_TASK_INDEX**. Obtain the environment variable using the method provided in the demo script for compatibility.
   -  Use V2 **${MA_VJ_NAME}-${MA_TASK_NAME}-0.${MA_VJ_NAME}:6666** to replace V1 **BATCH_CUSTOM0_HOSTS**.
   -  Use V2 **${MA_VJ_NAME}-${MA_TASK_NAME}-{N}.${MA_VJ_NAME}:6666** to replace V1 **BATCH_CUSTOM{N}_HOSTS** generally.

#. Check whether there are settings that allow concurrent reading and writing of the same file in the code. If so, modify the settings to forbid this operation.

   If a job uses multiple cards, the same code for reading and writing data may be available on each card. In this case, do as follows to modify the code:

   .. code-block::

      import moxing as mox
      from mindspore.communication import init, get_rank, get_group_size
      init()
      rank_id = get_rank()
      # Enable only card 0 to download data.
      if rank_id % 8 == 0:
          mox.file.copy_parallel('obs://bucket-name/dir1/dir2/', '/cache')

Summary and Suggestions
-----------------------

Before creating a training job, use the ModelArts development environment to debug the training code to maximally eliminate errors in code migration.

.. |image1| image:: /_static/images/en-us_image_0000001910008856.png
