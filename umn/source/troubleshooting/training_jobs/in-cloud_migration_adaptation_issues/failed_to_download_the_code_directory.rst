:original_name: modelarts_13_0023.html

.. _modelarts_13_0023:

Failed to Download the Code Directory
=====================================

Symptom
-------

The code directory fails to be downloaded during training job running, and the following error message is displayed. See :ref:`Figure 1 <en-us_topic_0000002340728060__fig920916392148>`.

.. code-block::

   ERROR: modelarts-downloader.py: Get object key failed: 'Contents'

.. _en-us_topic_0000002340728060__fig920916392148:

.. figure:: /_static/images/en-us_image_0000002374847081.png
   :alt: **Figure 1** Failure of getting content

   **Figure 1** Failure of getting content

Possible Cause
--------------

The code directory specified during training job creation does not exist. As a result, the training fails.

Solution
--------

Check whether the code directory specified during training job creation, that is, the OBS bucket path, is correct based on the error cause. There are two methods to check whether it exists.

-  Log in to the OBS management console using the current account, and search for the OBS buckets, folders, and files in the path to check whether the code directory exists.

-  Using APIs to check whether the directory exists: Run the following command in code to check whether the directory exists:

   .. code-block::

      import moxing as mox
      mox.file.exists('obs://obs-test/ModelArts/examples/')
