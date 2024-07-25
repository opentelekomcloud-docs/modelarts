:original_name: modelarts_23_0332.html

.. _modelarts_23_0332:

.. _en-us_topic_0000001915042052:

Uploading Data to JupyterLab
============================

On the **JupyterLab** page, click **Upload Files** to upload a file. For details, see :ref:`Uploading a File <en-us_topic_0000001946441181__en-us_topic_0000001799337328_en-us_topic_0208766071_section172463910383>` in :ref:`Introduction to JupyterLab and Common Operations <en-us_topic_0000001946441181>`. If a message is displayed indicating that the size of the files to be uploaded exceeds the upper limit when uploading files to notebook instances or JupyterLab, you can upload the files to OBS and then download them to notebook instances.

Step 1: Uploading Files to OBS
------------------------------

Use the OBS API to upload large files because OBS Console has restrictions on the file size and quantity.

Step 2: Downloading Files from OBS to Notebook Instances
--------------------------------------------------------

A notebook instance can be mounted to OBS or EVS as the storage location. The operation method varies depending on the instance types.

-  Downloading files to notebook instances with EVS attached

   -  Use the following MoXing API to synchronize files from OBS to notebook instances.

      Read an OBS file. For example, if you read the **obs://bucket_name/obs_file.txt** file, the content is returned as strings.

      ::

         import moxing as mox
         file_str = mox.file.read('obs://bucket_name/obs_file.txt')

      You can also open the file object and read data from it. Both methods are equivalent.

      ::

         import moxing as mox
         with mox.file.File('obs://bucket_name/obs_file.txt', 'r') as f:
           file_str = f.read()

   -  Use the OBS API in the ModelArts SDK to download data from OBS to notebook instances.

      .. note::

         If the size of a single file exceeds 5 GB, the file cannot be uploaded in this mode. Use the MoXing API to upload large files.

      Sample code:

      ::

         from modelarts.session import Session
         session = Session()
         session.download_data(bucket_path="/bucket-name/dir1/sdk.txt", path="/home/user/sdk/obs.txt")

-  Downloading files to notebook instances using OBS for data storage

   Upload files to the OBS path specified during notebook instance creation and synchronize the files from OBS to the notebook instances using Sync OBS.

Step 3: (Optional) Decompressing Files
--------------------------------------

If a file is uploaded to Notebook as a compressed package, you can decompress the package in Notebook Terminal.

.. code-block::

   unzip xxx.zip # Directly decompress the package in the path where the package is stored.

For more details, search for the decompression command in mainstream search engines.
