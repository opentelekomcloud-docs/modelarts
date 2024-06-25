:original_name: modelarts_05_0114.html

.. _modelarts_05_0114:

How Do I Improve Training Efficiency While Reducing Interaction with OBS?
=========================================================================

Scenario Description
--------------------

When ModelArts is used for custom deep learning training, training data is usually stored in OBS. If the volume of training data is large (for example, greater than 200 GB), a GPU resource pool is required for training each time, resulting in low training efficiency.

To improve training efficiency while reducing interaction with OBS, perform the following operations for optimization.

Optimization Principles
-----------------------

For the GPU resource pool provided by ModelArts, 500 GB NVMe SSDs are attached to each training node for free. The SSDs are attached to the **/cache** directory. The lifecycle of data in the **/cache** directory is the same as that of a training job. After the training job is complete, all content in the **/cache** directory is cleared to release space for the next training job. Therefore, you can copy data from OBS to the **/cache** directory during training so that data can be read from the **/cache** directory each time until the training is complete. After the training is complete, content in the **/cache** directory will be automatically cleared.

Optimization Methods
--------------------

TensorFlow code is used as an example.

The following is code before optimization:

::

   ...
   tf.flags.DEFINE_string('data_url', '', 'dataset directory.')
   FLAGS = tf.flags.FLAGS
   mnist = input_data.read_data_sets(FLAGS.data_url, one_hot=True)

The following is an example of the optimized code. Data is copied to the **/cache** directory.

::

   ...
   tf.flags.DEFINE_string('data_url', '', 'dataset directory.')
   FLAGS = tf.flags.FLAGS
   import moxing as mox
   TMP_CACHE_PATH = '/cache/data'
   mox.file.copy_parallel('FLAGS.data_url', TMP_CACHE_PATH)
   mnist = input_data.read_data_sets(TMP_CACHE_PATH, one_hot=True)
