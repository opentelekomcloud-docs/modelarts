:original_name: modelarts_05_0057.html

.. _modelarts_05_0057:

How Do I Import Large Files to a Notebook Instance?
===================================================

-  **Large files (files larger than 100 MB)**

   Use OBS to upload large files. To do so, use OBS Browser to upload a local file to an OBS bucket and use ModelArts SDK to download the file from OBS to a notebook instance.

   For details about how to use ModelArts SDK or MoXing to download files from OBS, see :ref:`How Do I Upload a File from a Notebook Instance to OBS or Download a File from OBS to a Notebook Instance? <modelarts_05_0024>`

-  **Folders**

   Compress a folder into a package and upload the package in the same way as uploading a large file. After the package is uploaded to a notebook instance, decompress it on the **Terminal** page.

   .. code-block::

      unzip xxx.zip # Directly decompress the package in the path where the package is stored.

   For more details, search for the decompression command in mainstream search engines.
