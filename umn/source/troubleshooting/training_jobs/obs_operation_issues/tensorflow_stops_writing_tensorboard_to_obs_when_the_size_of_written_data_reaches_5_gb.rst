:original_name: modelarts_13_0022.html

.. _modelarts_13_0022:

TensorFlow Stops Writing TensorBoard to OBS When the Size of Written Data Reaches 5 GB
======================================================================================

Symptom
-------

The following error message is displayed for a ModelArts training job:

.. code-block::

   Encountered Unknown Error EntityTooLarge
   Your proposed upload exceeds the maximum allowed object size.:

.. code-block::

   If the signature check failed. This could be because of a time skew. Attempting to adjust the signer

Possible Cause
--------------

The size of files to be uploaded at a time is limited to 5 GB in OBS. TensorFlow may save the summary file in local cache. Therefore, when flush is triggered each time, the summary file overwrites the original file on OBS. If the size of the file exceeds 5 GB, the file stops being written.

Solution
--------

If this problem occurs during the running of a training job, use the following method for troubleshooting.

#. You are advised to use the following local cache method:

   .. code-block::

      import moxing.tensorflow as mox
      mox.cache()
