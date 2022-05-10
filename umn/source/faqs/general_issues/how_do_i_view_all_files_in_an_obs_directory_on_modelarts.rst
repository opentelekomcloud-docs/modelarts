:original_name: modelarts_21_0058.html

.. _modelarts_21_0058:

How Do I View All Files in an OBS Directory on ModelArts?
=========================================================

To view all files stored in OBS when using notebook instances or training jobs, use either of the following methods:

-  OBS console

   Log in to OBS console using the current account, and search for the OBS buckets, folders, and files.

-  You can use an API to check whether a given directory exists. In an existing notebook instance or after creating a new notebook instance, run the following command to check whether the directory exists:

   .. code-block::

      import moxing as mox
      mox.file.list_directory('obs://bucket_name', recursive=True)

   If there are a large number of files, wait until the final file path is displayed.
