:original_name: modelarts_13_0039.html

.. _modelarts_13_0039:

Failed to Find a File in a Training Job
=======================================

Symptom
-------

The following error occurs in the ModelArts training job log:

FileNotFoundError:[Errno 2]No such file or directory:'data_v.pickle'


.. figure:: /_static/images/en-us_image_0000001799498944.png
   :alt: **Figure 1** Log error

   **Figure 1** Log error

Possible Cause
--------------

According to the error message, the file path is incorrect, and the user uses the relative path of the file. As a result, the error occurs.

Solution
--------

To address this issue, perform the following operations:

#. According to the error location **with open("data_v.pickle","rb") as f:** , a relative path is used. The path is the relative path of the current container location, that is, **/home/work/user-job-dir**. Check whether the path exists.
#. If the path is an OBS path, use the following method to access it. Assume that the path is **obs://bucket_name/data_v.pickle**.

   a. Use MoXing for switching.

      .. code-block::

         import os
         import moxing as mox

         mox.file.shift('os', 'mox')

         with open('obs://bucket_name/data_v.pickle') as f:
         print(f.read())

   b. Copy data to the container and use the path in the container to read and write data. The following is the method for copying data to the container.

      .. code-block::

         import moxing as mox
         mox.file.make_dirs('/cache/data')

         mox.file.copy('obs://bucket_name/data_v.pickle','/cache/data/data_v.pickle')

         with open('/cache/data/data_v.pickle') as f:
         print(f.read())
