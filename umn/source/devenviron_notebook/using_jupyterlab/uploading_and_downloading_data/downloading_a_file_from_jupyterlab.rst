:original_name: modelarts_23_0333.html

.. _modelarts_23_0333:

Downloading a File from JupyterLab
==================================

Only files within 100 MB in JupyterLab can be downloaded to a local PC. You can perform operations in different scenarios based on the storage location selected when creating a notebook instance.

Notebook Instances Using OBS Storage
------------------------------------

For notebook instances that use OBS storage, you can use OBS or the ModelArts SDK to download files from OBS to a local PC.

-  Method 1: Downloading the files using OBS

   Use OBS to download the files to the local PC. If you have a large amount of data, use OBS Browser+ to download data or folders.

-  Method 2: Downloading the files using the ModelArts SDKs

   #. Download and install the ModelArts SDKs on your local PC. For details, see .

   #. Authenticate sessions of the ModelArts SDKs. For details, see .

   #. from OBS to the local PC. The sample code is as follows:

      .. code-block::

         from modelarts.session import Session
         session=Session(access_key='***',secret_key='***',project_id='***',region_name='***')
         session.download_data(bucket_path="/bucket_name/obs_file.txt",path="/home/user/obs_file.txt")
