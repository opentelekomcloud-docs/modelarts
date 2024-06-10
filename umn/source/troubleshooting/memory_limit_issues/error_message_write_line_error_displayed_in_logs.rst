:original_name: modelarts_trouble_0031.html

.. _modelarts_trouble_0031:

Error Message "write line error" Displayed in Logs
==================================================

Symptom
-------

During the program's execution, numerous "write line error" messages are generated. This issue recurred each time the program ran at a specific progress.


.. figure:: /_static/images/en-us_image_0000001846057389.png
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

.. _modelarts_trouble_0031__en-us_topic_0000001192868375_en-us_topic_0000001135764558_en-us_topic_0192056517_section520813413313:

Solution
--------

#. If the issue is caused by core files, add the following code at the very beginning of the boot script to disable the generation of the core files:

   .. code-block::

      import os
      os.system("ulimit -c 0")

#. Check whether the dataset and checkpoint file have used up the storage space of the **/cache** directory.

#. Use the local PyCharm to remotely connect to the notebook for debugging.

Summary and Suggestions
-----------------------

Before creating a training job, use the ModelArts development environment to debug the training code to maximally eliminate errors in code migration.
