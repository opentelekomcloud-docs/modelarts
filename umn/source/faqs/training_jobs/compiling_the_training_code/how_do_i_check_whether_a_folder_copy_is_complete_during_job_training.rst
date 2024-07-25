:original_name: modelarts_05_0092.html

.. _modelarts_05_0092:

How Do I Check Whether a Folder Copy Is Complete During Job Training?
=====================================================================

In the script for training job boot file, run the following commands to obtain the sizes of the copied folders and the folders to be copied. Then determine whether folder copy is complete based on the command output.

.. code-block::

   import moxing as mox
   mox.file.get_size('obs://bucket_name/obs_file',recursive=True)

**get_size** indicates the size of the file or folder to be obtained. **recursive=True** indicates that the type is folder. **True** indicates that the type is folder, and **False** indicates that the type is file.

If the command output is consistent, the folder copy is complete. If the command output is inconsistent, the folder copy is not complete.
