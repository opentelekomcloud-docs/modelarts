.. _modelarts_23_0333:

Downloading a File from JupyterLab
==================================

Only files within 100 MB in JupyterLab can be downloaded to a local PC. You can perform operations in different scenarios based on the storage location selected when creating a notebook instance.

Notebook Instances with EVS Attached
------------------------------------

For notebook instances with EVS attached, you can perform the following operations to download large files to the local PC:

#. In the notebook instance, create an **ipynb** file. Use MoXing to upload the large files from notebook instances to OBS. The sample code is as follows:

   +-----------------------------------+---------------------------------------------------------------------------------------+
   | ::                                | ::                                                                                    |
   |                                   |                                                                                       |
   |    1                              |    import moxing as mox                                                               |
   |    2                              |    mox.file.copy('/home/ma-user/work/obs_file.txt', 'obs://bucket_name/obs_file.txt') |
   +-----------------------------------+---------------------------------------------------------------------------------------+

   In the preceding code, **/home/ma-user/work/obs_file.txt** indicates a file storage path in a notebook instance, and **obs://bucket_name/obs_file.txt** indicates a file storage path on OBS.

#. Use OBS or the ModelArts SDKs to download the files from OBS to the local PC.

Notebook Instances Using OBS Storage
------------------------------------

For notebook instances that use OBS storage, you can use OBS or the ModelArts SDK to download files from OBS to a local PC.

Use OBS for download.
