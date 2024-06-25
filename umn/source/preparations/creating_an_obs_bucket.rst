:original_name: modelarts_08_0003.html

.. _modelarts_08_0003:

Creating an OBS Bucket
======================

ModelArts uses OBS to store data and model backups and snapshots, achieving secure, reliable, and low-cost storage. Before using ModelArts, create an OBS bucket and folders for storing data.

OBS
---

OBS provides stable, secure, and efficient cloud storage service that lets you store virtually any volume of unstructured data in any format. Bucket and objects are basic concepts in OBS. A bucket is a container for storing objects in OBS. Each bucket is specific to a region and has specific storage class and access permissions. A bucket is accessible through its domain name over the Internet. An object is the basic unit of data storage in OBS.

ModelArts cannot store data and uses OBS as its data storage center. All the input data, output data, and cache data during AI development can be stored in OBS buckets for reading.

Before using ModelArts, create an OBS bucket and folders for storing data.


.. figure:: /_static/images/en-us_image_0000001910055454.png
   :alt: **Figure 1** OBS

   **Figure 1** OBS

Procedure
---------

#. Log in to OBS Console and click **Create Bucket** in the upper right corner of the page to create an OBS bucket. For example, create an OBS bucket named **c-flowers**.

   .. note::

      The created OBS bucket and ModelArts are in the same region.

      Do not enable **Default Encryption**. ModelArts cannot read the data from encrypted OBS buckets.

#. On the **Buckets** page, click the bucket name to view its details.

#. Click **Objects** in the navigation pane on the left. On the **Objects** page, click **Create Folder** to create an OBS folder. For example, create a folder named **flowers** in the created **c-flowers** OBS bucket. For details, see "Creating a Folder".


   .. figure:: /_static/images/en-us_image_0000001919561582.png
      :alt: **Figure 2** Create Folder

      **Figure 2** Create Folder

FAQs
----

-  Why cannot I find my created OBS bucket when I select an OBS path in ModelArts?

   The created OBS bucket and ModelArts are not in the same region.

-  How do I check whether ModelArts and an OBS bucket are in the same region?

   #. Check the region where the created OBS bucket is located.

      a. Log in to the OBS management console.

      b. On the **Object Storage Service** page, enter a keyword in **Bucket Name** to search for a bucket.

         In the **Region** column, view the region where the created OBS bucket is located.

   #. Check the region where ModelArts is deployed.

      Log in to the ModelArts management console and view the region where ModelArts is located in the upper left corner.

   #. Check whether the region of the created OBS bucket is the same as that of ModelArts. Ensure that they are the same.
