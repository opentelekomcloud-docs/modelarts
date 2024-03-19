:original_name: modelarts_08_0003.html

.. _modelarts_08_0003:

Creating an OBS Bucket
======================

ModelArts uses OBS to store data, and backs up and takes snapshots for models, achieving secure, reliable storage at low costs. Before using ModelArts, create an OBS bucket and folders for storing data.

OBS
---

OBS provides stable, secure, and efficient cloud storage service that lets you store virtually any volume of unstructured data in any format. Bucket and objects are basic concepts in OBS. A bucket is a container for storing objects in OBS. Each bucket is specific to a region and has specific storage class and access permissions. A bucket is accessible through its domain name over the Internet. An object is the basic unit of data storage in OBS.

OBS is a data storage center for ModelArts. All the input data, output data, and cache data during AI development can be stored in OBS buckets for reading.

Therefore, before using ModelArts, create an OBS bucket with folders for storing data.


.. figure:: /_static/images/en-us_image_0000001846137953.png
   :alt: **Figure 1** OBS

   **Figure 1** OBS

Procedure
---------

#. Log in to the OBS console and click **Create Bucket** in the upper right corner of the page to create an OBS bucket. For example, create an OBS bucket named **ei-cloud**.

   .. note::

      The created OBS bucket and ModelArts must be in the same region.

      Do not enable **Default Encryption**. ModelArts cannot read the data from encrypted OBS buckets.

#. On the **Buckets** page, click the bucket name to view its details.


   .. figure:: /_static/images/en-us_image_0000001851792033.png
      :alt: **Figure 2** Buckets

      **Figure 2** Buckets

#. Click **Objects** in the navigation pane on the left. On the **Objects** page, click **Create Folder** to create an OBS folder. For example, create a folder named **flowers** in the created **ei-cloud** OBS bucket. For details, see Creating a Folder.


   .. figure:: /_static/images/en-us_image_0000001851792857.png
      :alt: **Figure 3** Creating a folder

      **Figure 3** Creating a folder
