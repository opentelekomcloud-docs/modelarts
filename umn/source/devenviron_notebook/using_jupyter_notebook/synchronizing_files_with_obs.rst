.. _modelarts_23_0038:

Synchronizing Files with OBS
============================

If you specify **Storage Path** during notebook instance creation, your compiled code will be automatically stored in your specified OBS bucket. If code invocation among different **.ipynb** files is required, you can use the Sync OBS function.

The Sync OBS function is used to synchronize the objects selected in the list of notebook instance files from the OBS bucket to the current container directory **~/work**.

Precautions
-----------

-  The maximum size of files to be synchronized at a time is 500 MB, and the maximum number of files to be synchronized at a time is 1,024.
-  The total size of objects to be synchronized cannot exceed 5 GB. For example, if 2 GB files exist in the **~/work** container directory, you can use Sync OBS to synchronize a maximum of 3 GB files.
-  The Sync OBS function only takes effect on notebook instances for which **Storage** is **OBS**. For notebook instances whose **Storage** is not **OBS**, all files are read and written in the **~/work** container directory.

Procedure
---------

The Sync OBS function can be used in notebook instances. The following describes how to use the function.

For example, if the **Example1.ipynb** file needs to call **module** in the **Example2.ipynb** file, select both files and click **Sync OBS**.

.. _modelarts_23_0038__en-us_topic_0164900253_fig4940114710298:

.. figure:: /_static/images/en-us_image_0000001156920981.png
   :alt: **Figure 1** Using the Sync OBS function


   **Figure 1** Using the Sync OBS function
