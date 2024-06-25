:original_name: modelarts_trouble_0042.html

.. _modelarts_trouble_0042:

Error Message "BrokenPipeError: Broken pipe" Displayed When OBS Data Is Copied
==============================================================================

Symptom
-------

The error message is displayed when MoXing is used to copy data for a training job.


.. figure:: /_static/images/en-us_image_0000001910009244.png
   :alt: **Figure 1** Error log

   **Figure 1** Error log

Possible Causes
---------------

The possible causes are as follows:

-  In a large-scale distributed job, multiple nodes are concurrently copying files in the same bucket, leading to traffic control in the OBS bucket.
-  There is a large number of OBS client connections. During the polling between processes or threads, an OBS client connection timed out if the server does not respond to it within 30 seconds. As a result, the server released the connection.

Solution
--------

#. If the issue is caused by traffic control, the error code shown in the following figure is displayed. In this case, submit a service ticket. For details about OBS error codes, see **Python > Troubleshooting > OBS Server-Side Error Codes** in *Object Storage Service SDK Reference*.


   .. figure:: /_static/images/en-us_image_0000001943968433.png
      :alt: **Figure 2** Error log

      **Figure 2** Error log

#. If the issue is caused by the large number of client connections, especially for files larger than 5 GB, OBS APIs cannot be directly called. In this case, use multiple threads to copy data. The timeout duration set on the OBS server is 30s. Run the following commands to reduce the number of processes:

   .. code-block::

      # Configure the number of processes.
      os.environ['MOX_FILE_LARGE_FILE_TASK_NUM']=1
      import moxing as mox

      # Copy files.
      mox.file.copy_parallel(src_url=your_src_dir, dst_url=your_target_dir, threads=0, is_processing=False)

   .. note::

      When creating a training job, you can use the environment variable **\_PARTIAL_MAXIMUM_SIZE** to configure the threshold (in bytes) for downloading large files in multiple parts. If the size of a file exceeds the threshold, the file will be downloaded in multiple parts concurrently.

Summary and Suggestions
-----------------------

Before creating a training job, use the ModelArts development environment to debug the training code to maximally eliminate errors in code migration.
