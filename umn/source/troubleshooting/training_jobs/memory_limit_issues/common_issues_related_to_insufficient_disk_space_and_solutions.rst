:original_name: modelarts_trouble_0142.html

.. _modelarts_trouble_0142:

Common Issues Related to Insufficient Disk Space and Solutions
==============================================================

This section centrally describes common issues related to insufficient disk space and solutions to these issues.

Symptom
-------

When data, code, or model is copied during training, error message "No space left on device" is displayed.


.. figure:: /_static/images/en-us_image_0000002233900040.png
   :alt: **Figure 1** Error log

   **Figure 1** Error log

Possible Causes
---------------

The possible causes are as follows:

-  The storage space in the **/cache** directory is used up by the local data and files stored in it.
-  Data is decompressed when being processed. As a result, the data volume increases, and finally the storage space in the **/cache** directory is used up.
-  Data is not saved in **/cache** or **/home/ma-user/** (**/cache** will be softly connected to **/home/ma-user/**). As a result, the system directory is fully occupied. The system directory supports only basic running of system functions. It cannot be used to store large volumes of data.
-  During the training of certain jobs, checkpoint files will be generated and updated. If historical checkpoint files are not deleted after an update, the **/cache** directory will be exhausted.
-  The storage space is sufficient, but the error message "No Space left on device" is still displayed. This may be triggered by an error in the file index cache of the operating system. As a result, no file can be created in the system disk, and finally data disks are used up.

   .. note::

      The conditions for triggering an error in the file index cache are as follows:

      -  A longer file name leads to a smaller upper limit for the number of files.
      -  A smaller block size leads to a smaller upper limit for the number of files. (There are three block sizes, 1024 bytes, 2048 bytes, and 4096 bytes. The default size is 4096 bytes.)
      -  This issue is more likely to occur if files are created in a shorter period of time. The reason is as follows: There is a cache, the size of which is determined based on the preceding two factors. When the number of files in the directory is large, the cache will be enabled and released with the files.

-  Core files are generated during the program running and exhaust the storage space in the **/** root directory.

Solution
--------

#. Obtain the sizes of the dataset, decompressed dataset, and checkpoint file and check whether they have exhausted the disk space.

#. If the volume of data exceeds the **/cache** size, use SFS to attach more data disks for expanding the storage size.

#. Save the data and checkpoint in **/cache** or **/home/ma-user/**.

#. Check the checkpoint logic and ensure that historical checkpoints are deleted so that they will not use up the storage space in **/cache**.

#. If the file size is smaller than the **/cache** size, and the number of files exceeds 500,000, the issue may be caused by an error in the file index cache of the operating system. In this case, do as follows to resolve this issue:

   -  Reduce the number of files in a single directory.
   -  Slow down the file creation speed. For example, during data decompression, add a sleep period of 5s before decompressing the next piece of data.

#. If the issue is caused by core files, add the following code at the very beginning of the boot script to disable the generation of the core files (debug code in a development environment before adding the code):

   .. code-block::

      import os
      os.system("ulimit -c 0")

Summary and Suggestions
-----------------------

Before creating a training job, use the ModelArts development environment to debug the training code to maximally eliminate errors in code migration.
