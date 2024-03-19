:original_name: modelarts_30_0046.html

.. _modelarts_30_0046:

Uploading a Local File with a Size Ranging from 100 MB to 5 GB to JupyterLab
============================================================================

For a file that exceeds 100 MB but does not exceed 5 GB, upload the file to OBS (an object bucket or a parallel file system), and then download the file from OBS to the target notebook instance. After the download is complete, the file is automatically deleted from OBS.

Upload a local file with a size ranging from 100 MB to 5 GB to JupyterLab through OBS.

To upload a large file through OBS, set an OBS path.

-  Method 1: Enter a valid OBS path in the text box and click **OK**.

-  Method 2: Select an OBS path in **OBS File Browser** and click **OK**.

-  Method 3: Use the default path.

**Decompressing a package**

After a large file is uploaded to Notebook JupyterLab as a compressed package, you can decompress the package in Terminal.

.. code-block::

   unzip xxx.zip  # Directly decompress the package in the path where the package is stored.

For more details, search for the decompression command in mainstream search engines.
