:original_name: modelarts_21_0079.html

.. _modelarts_21_0079:

How Do I Check Whether Folder Copy Is Complete During Job Training?
===================================================================

In the script of the training job boot file, run the following commands to obtain the sizes of the to-be-copied and copied folders. Then determine whether folder copy is complete based on the command output.

.. code-block::

   import moxing as mox
   mox.file.get_size('obs://bucket_name/obs_file',recursive=True)

**get_size** indicates the size of the file or folder to be obtained. **recursive=True** indicates that the type is folder. **True** indicates that the type is folder, and **False** indicates that the type is file.

If the command output is consistent, the folder copy is complete. If the command output is inconsistent, the folder copy is not complete.
