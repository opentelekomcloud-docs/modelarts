:original_name: modelarts_13_0038.html

.. _modelarts_13_0038:

Failed to Access a Folder Using MoXing and Read the Folder Size Using get_size
==============================================================================

Symptom
-------

-  The folder cannot be accessed using MoXing.
-  The folder size read by using **get_size** of MoXing is 0.

Possible Cause
--------------

To use MoXing to access a folder, you need to add the **recursive=True** parameter. The default value is **False**.

Solution
--------

Obtain the size of an OBS folder.

.. code-block::

   mox.file.get_size('obs://bucket_name/sub_dir_0/sub_dir_1', recursive=True)

Obtain the size of an OBS file.

.. code-block::

   mox.file.get_size('obs://bucket_name/obs_file.txt')
