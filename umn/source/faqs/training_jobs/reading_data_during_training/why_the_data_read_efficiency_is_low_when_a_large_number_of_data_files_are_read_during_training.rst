:original_name: modelarts_05_0236.html

.. _modelarts_05_0236:

Why the Data Read Efficiency Is Low When a Large Number of Data Files Are Read During Training?
===============================================================================================

If a dataset contains a large number of data files (massive small files) and data is stored in OBS, files need to be repeatedly read from OBS during training. As a result, the training process is waiting for reading files, resulting in low read efficiency.

Solution
--------

#. Compress the massive small files into a package on your local PC, for example, a .zip package.

#. Upload the package to OBS.

#. During training, directly download this package from OBS to the **/cache** directory of your local PC. Perform this operation only once.

   For example, you can use mox.file.copy_parallel to download the .zip package to the **/cache** directory, decompress the package, and then read files for training.

   ::

      ...
      tf.flags.DEFINE_string('<obs_file_path>/data.zip', '', 'dataset directory.')
      FLAGS = tf.flags.FLAGS
      import os
      import moxing as mox
      TMP_CACHE_PATH = '/cache/data'
      mox.file.copy_parallel('FLAGS.data_url', TMP_CACHE_PATH)
      zip_data_path = os.path.join(TMP_CACHE_PATH, '*.zip')
      unzip_data_path = os.path.join(TEMP_CACHE_PATH, 'unzip')
      # You can also decompress .zip Python packages.
      os.system('unzip '+ zip_data_path + ' -d ' + unzip_data_path))
      mnist = input_data.read_data_sets(unzip_data_path, one_hot=True)
