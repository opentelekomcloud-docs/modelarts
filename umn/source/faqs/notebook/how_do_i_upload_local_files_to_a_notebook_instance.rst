:original_name: modelarts_21_0068.html

.. _modelarts_21_0068:

How Do I Upload Local Files to a Notebook Instance?
===================================================

-  **Small files (files smaller than 100 MB)**

   Open a notebook instance and click **Upload** in the upper right corner to upload a local file to the notebook instance.


   .. figure:: /_static/images/en-us_image_0000001235505840.png
      :alt: **Figure 1** Upload a small file

      **Figure 1** Upload a small file

-  **Large files (files larger than 100 MB)**

   You are advised to use OBS to upload large files. Use OBS Browser to upload a local file to an OBS bucket and use ModelArts SDKs to download the file from OBS to a notebook instance.

   To upload files using OBS Browser, refer to `Uploading a File <https://docs.otc.t-systems.com/en-us/usermanual/obs/obs_03_0307.html>`__.

   To use ModelArts SDKs to download files from OBS to a notebook instance, refer to `Downloading a File from OBS <https://docs.otc.t-systems.com/en-us/sdkreference/modelarts/modelarts_04_0220.html>`__.

-  **Folders**

   Compress a folder into a package and upload the package in the same way as uploading a large file. After the package is uploaded to a notebook instance, decompress it on the **Terminal** page.
