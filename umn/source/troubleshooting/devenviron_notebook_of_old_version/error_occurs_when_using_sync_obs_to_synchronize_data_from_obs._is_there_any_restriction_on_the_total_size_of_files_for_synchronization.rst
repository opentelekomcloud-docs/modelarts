:original_name: modelarts_13_0004.html

.. _modelarts_13_0004:

Error Occurs When Using Sync OBS to Synchronize Data from OBS. Is There Any Restriction on the Total Size of Files for Synchronization?
=======================================================================================================================================

Symptom
-------

The following error occurs when synchronizing data from OBS to a notebook instance: **obs sync failed**. As a result, the notebook instance cannot be used properly.

Possible Cause
--------------

If you set **Storage** to OBS when creating a notebook instance, all files in the notebook instance are stored in the OBS directory. If you want to use the files, you must use the Sync OBS function to synchronize the files from OBS to the **~/work** directory of the notebook instance.

-  A maximum of 1,024 files can be synchronized at a time.
-  The total size of objects (including those synchronized and to be synchronized) cannot exceed 5 GB. A maximum of 500 MB objects can be synchronized at a time. For example, if there are 200 MB files in the **~/work** container directory, a maximum of 300 MB files can be synchronized at a time using the Sync OBS function.
-  The Sync OBS function only takes effect on notebook instances for which **Storage** is **OBS**. For notebook instances whose **Storage** is not **OBS**, all files are read and written in the **~/work** container directory.

Solution
--------

The error message indicates that the size of files synchronized at a time exceeds the upper limit.

#. If the number of files to be synchronized at a time exceeds 1024, synchronize them at twice.
#. If the sum of the size of the files to be synchronized and the size of the files in the **/home/ma-user/work** directory is greater than 500 MB, clear space in the directory and synchronize the files again.
