:original_name: modelarts_trouble_0041.html

.. _modelarts_trouble_0041:

Error Message "No space left on device" Displayed in Logs
=========================================================

Symptom
-------

When data, code, or a model was copied during training, the following error message was displayed.


.. figure:: /_static/images/en-us_image_0000001846057481.png
   :alt: **Figure 1** Error log

   **Figure 1** Error log

Possible Causes
---------------

The possible causes are as follows:

-  The disk space is insufficient.

-  When a distributed job is executed, the **docker base size** configuration does not take effect on certain nodes. As a result, the storage space of the **/** root directory in the container is only the default value of 10 GB, which should be 50 GB, leading to the job training failure.

-  The storage space is sufficient, but the error message "No Space left on device" is still displayed.

   If there are a large number of files in the same directory, the kernel creates an index table to accelerate file retrieval. If a large number of files are created in a short period of time, the number of indexes reaches the upper limit, and an error occurs.

   .. note::

      The issue occurs depending on the following factors:

      -  A longer file name leads to a smaller upper limit for the number of files.
      -  A smaller block size leads to a smaller upper limit for the number of files. The block size can be 1024 bytes, 2048 bytes, or 4096 bytes, and it defaults to 4096 bytes.
      -  The issue is more likely to occur if files are created in a shorter period of time. The reason is as follows: There is a cache, the size of which is determined based on the preceding two factors. When the number of files in the directory is large, the cache is enabled. The resources are released if they are not used.

.. _modelarts_trouble_0041__en-us_topic_0000001192988243_en-us_topic_0000001136263284_en-us_topic_0192056517_section520813413313:

Solution
--------

#. Rectify the fault by following the operations described in :ref:`Error Message "write line error" Displayed in Logs <modelarts_trouble_0031>`.
#. If the issue occurs only on certain nodes used by the distributed job, submit a service ticket to isolate the faulty nodes.
#. If the issue is caused by EulerOS restrictions, take the following measures:

   -  Reduce the number of files in a single directory.
   -  Slow down the file creation speed.
   -  Disable the dir_index attribute of the Ext4 file system. For details, see `What is the meaning of "ext[3/4]_dx_add_entry: Directory index full!"? <https://access.redhat.com/solutions/29894>`__

Summary and Suggestions
-----------------------

Before creating a training job, use the ModelArts development environment to debug the training code to maximally eliminate errors in code migration.
