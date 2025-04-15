:original_name: modelarts_13_0018.html

.. _modelarts_13_0018:

Failed to Correctly Read Files
==============================

Symptom
-------

-  How to read the **json** and **npy** files when creating a training job.

-  How the training job uses the cv2 library to read files.

-  How to use the torch package in the MXNet environment.

-  The following error occurs when the training job reads the file:

   .. code-block::

      NotFoundError (see above for traceback): Unsucessful TensorSliceReader constructor: Failed to find any matching files for xxx://xxx

Possible Cause
--------------

In ModelArts, user's data is stored in OBS buckets, but training jobs are running in containers. Therefore, users cannot access files in OBS buckets by accessing local paths.

Solution
--------

If an error occurs when you read a file, you can use MoXing to copy data to a container and then access the data in the container. For details, see :ref:`1 <en-us_topic_0000002233739636__li0773121693319>`.

You can also read files based on the file type. For details, see :ref:`Reading .json files <en-us_topic_0000002233739636__li1489841103613>`, :ref:`Reading .npy files <en-us_topic_0000002233739636__li19472171513369>`, and :ref:`Using the cv2 library to read files <en-us_topic_0000002233739636__li13209101919362>`, and :ref:`Using the torch package in the MXNet environment <en-us_topic_0000002233739636__li476001011517>`.

#. .. _en-us_topic_0000002233739636__li0773121693319:

   If an error occurs when you read a file, you can use MoXing to copy data to a container and then access the data in the container as follows:

   .. code-block::

      import moxing as mox
      mox.file.make_dirs('/cache/data_url')
      mox.file.copy_parallel('obs://bucket-name/data_url', '/cache/data_url')

#. .. _en-us_topic_0000002233739636__li1489841103613:

   To **read .\ **json** files**, run the following code:

   .. code-block::

      json.loads(mox.file.read(json_path, binary=True))

#. .. _en-us_topic_0000002233739636__li19472171513369:

   To **use **numpy.load** to read .\ **npy** files**, run the following code:

   -  Using the MoXing API to read files from OBS

      .. code-block::

         np.load(mox.file.read(_SAMPLE_PATHS['rgb'], binary=True))

   -  Using the file module of MoXing to read and write OBS files

      .. code-block::

         with mox.file.File(_SAMPLE_PATHS['rgb'], 'rb') as f:
         np.load(f)

#. .. _en-us_topic_0000002233739636__li13209101919362:

   To **use the cv2 library to read files**, run the following code:

   .. code-block::

      cv2.imdecode(np.fromstring(mox.file.read(img_path), np.uint8), 1)

#. .. _en-us_topic_0000002233739636__li476001011517:

   To **use the torch package in the MXNet environment**, run the following code:

   .. code-block::

      import os
      os.sysytem('pip install torch')
      import torch
