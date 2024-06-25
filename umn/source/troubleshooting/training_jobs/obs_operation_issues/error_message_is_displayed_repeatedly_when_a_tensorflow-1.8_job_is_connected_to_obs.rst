:original_name: modelarts_13_0019.html

.. _modelarts_13_0019:

Error Message Is Displayed Repeatedly When a TensorFlow-1.8 Job Is Connected to OBS
===================================================================================

Symptom
-------

After a training job is started based on TensorFlow-1.8 and the **tf.gfile** module is used to connect to OBS in code, the following log information is frequently printed:

.. code-block::

   Connection has been released. Continuing.
   Found secret key

Possible Cause
--------------

This problem occurs in TensorFlow-1.8. This log is of the INFO level and is not error information. You can set an environment variable to shield logs of the INFO level. The environment variable must be set before the **import tensorflow** or **import moxing** command is executed.

Solution
--------

Set the environment variable **TF_CPP_MIN_LOG_LEVEL** in code to shield logs of the INFO level. Detailed operations are as follows:

.. code-block::

   import os

   os.environ['TF_CPP_MIN_LOG_LEVEL'] = '2'

   import tensorflow as tf
   import moxing.tensorflow as mox

The mapping between **TF_CPP_MIN_LOG_LEVEL** and log levels is as follows:

.. code-block::

   import os
   os.environ["TF_CPP_MIN_LOG_LEVEL"]='1'     # Default level of logs to be displayed. All information is displayed.
   os.environ["TF_CPP_MIN_LOG_LEVEL"]='2'     # Only warning and error information is displayed.
   os.environ["TF_CPP_MIN_LOG_LEVEL"]='3'     # Only error information is displayed.
