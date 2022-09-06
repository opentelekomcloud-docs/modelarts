:original_name: modelarts_23_0332.html

.. _modelarts_23_0332:

Uploading Data to JupyterLab
============================

On the **JupyterLab** page, click **Upload Files** to upload a file. For details, see :ref:`Uploading a File <modelarts_23_0209__en-us_topic_0208766071_section172463910383>` in :ref:`Introduction to JupyterLab and Common Operations <modelarts_23_0209>`. If a message is displayed indicating that the size of the files to be uploaded exceeds the upper limit when uploading files to notebook instances or JupyterLab, you can upload the files to OBS and then download them to notebook instances.

Step 1: Uploading Files to OBS
------------------------------

Use the OBS API to upload large files because OBS Console has restrictions on the file size and quantity.

Step 2: Downloading Files from OBS to Notebook Instances
--------------------------------------------------------

A notebook instance can be mounted to OBS or EVS as the storage location. The operation method varies depending on the instance types.

-  Downloading files to notebook instances with EVS attached

   -  Read an OBS file. For example, if you read the **obs://bucket_name/obs_file.txt** file, the content is returned as strings.

      .. code-block::

         file_str = mox.file.read('obs://bucket_name/obs_file.txt')

      You can also open the file object and read data from it. Both methods are equivalent.

      .. code-block::

         with mox.file.File('obs://bucket_name/obs_file.txt', 'r') as f:
           file_str = f.read()

   -  Use the OBS API in the ModelArts SDK to download data to notebook instances.

      .. note::

         If the size of a single file exceeds 5 GB, the file cannot be uploaded in this mode. Use the MoXing API to upload large files.

      Sample code:

      .. code-block::

         from modelarts.session import Session
         session = Session()
         session.download_data(bucket_path="/bucket-name/dir1/sdk.txt", path="/home/user/sdk/obs.txt")

-  Downloading files to notebook instances using OBS for data storage

   Upload files to the OBS path specified during notebook instance creation and synchronize the files from OBS to the notebook instances using Sync OBS.
