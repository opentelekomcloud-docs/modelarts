:original_name: modelarts_05_0085.html

.. _modelarts_05_0085:

How Do I Rename an OBS File?
============================

OBS files cannot be renamed on the OBS console. To rename an OBS file, call a MoXing API in an existing or newly created notebook instance.

The following shows an example:

Rename **obs_file.txt** **obs_file_2.txt**.

.. code-block::

   import moxing as mox
   mox.file.rename('obs://bucket_name/obs_file.txt', 'obs://bucket_name/obs_file_2.txt')
