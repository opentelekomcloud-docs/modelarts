:original_name: modelarts_08_0003.html

.. _modelarts_08_0003:

Creating an OBS Bucket
======================

ModelArts uses OBS to store data and model backups and snapshots, achieving secure, reliable, and low-cost storage. Therefore, before using ModelArts, create an OBS bucket and folders for storing data.

Procedure
---------

#. Log in to OBS Console and create an OBS bucket. For details, see `Creating a Bucket <https://docs.otc.t-systems.com/en-us/usermanual/obs/en-us_topic_0045853662.html>`__. For example, create an OBS bucket named **c-flowers**.

   .. note::

      The created OBS bucket and ModelArts are in the same region.

#. Create a folder for storing data. For details, see `Creating a Folder <https://docs.otc.t-systems.com/en-us/usermanual/obs/obs_03_0316.html>`__. For example, create a folder named **flowers** in the created **c-flowers** OBS bucket.
