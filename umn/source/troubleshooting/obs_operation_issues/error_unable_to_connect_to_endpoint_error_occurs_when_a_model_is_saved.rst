:original_name: modelarts_13_0020.html

.. _modelarts_13_0020:

Error "Unable to connect to endpoint" Error Occurs When a Model Is Saved
========================================================================

Symptom
-------

An error occurs in the log when a model is saved in a training job. The error details are as follows:

InternalError (see above for traceback): : Unable to connect to endpoint

Possible Cause
--------------

When OBS connections are unstable, the following error may occur: **Unable to connect to endpoint**

Solution
--------

Add code to solve the problem of unstable OBS connections. You can add the following code at the beginning of the existing code so that TensorFlow can read and write ckpt and summary information in local cache mode:

.. code-block::

   import moxing.tensorflow as mox

   mox.cache()
