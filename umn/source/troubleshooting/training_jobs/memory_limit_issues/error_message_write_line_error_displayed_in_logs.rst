:original_name: modelarts_trouble_0031.html

.. _modelarts_trouble_0031:

Error Message "write line error" Displayed in Logs
==================================================

Symptom
-------

During program running, a large number of error messages "write line error" are generated. This issue recurs each time the program runs at a specific progress.


.. figure:: /_static/images/en-us_image_0000002374727525.png
   :alt: **Figure 1** Error log

   **Figure 1** Error log

Possible Causes
---------------

The possible causes are as follows:

-  Core files are generated during the program running and exhaust the storage space in the **/** root directory.
-  The 3.5 TB of storage space in the **/cache** directory is used up by the local data and files stored in it.

.. note::

   The disk space for in-cloud training consists of the space from the following directories:

   #. The **/** root directory, which is specified by **base size** in Docker. The default value is 10 GB. On the cloud, the value has been changed to 50 GB.
   #. The **/cache** directory, which is 3.5 TB typically.

Solution
--------

#. If the issue is caused by core files, add the following code at the very beginning of the boot script to disable the generation of the core files:

   .. code-block::

      import os
      os.system("ulimit -c 0")

#. Check whether the dataset and checkpoint file have used up the storage space of the **/cache** directory.

#. Use the local PyCharm to remotely access notebook for debugging.

Summary and Suggestions
-----------------------

Before creating a training job, use the ModelArts development environment to debug the training code to maximally eliminate errors in code migration.
