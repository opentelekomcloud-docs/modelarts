:original_name: modelarts_23_0333.html

.. _modelarts_23_0333:

.. _en-us_topic_0000001946441185:

Downloading a File from JupyterLab
==================================

Only files within 100 MB in JupyterLab can be downloaded to a local PC. You can perform operations in different scenarios based on the storage location selected when creating a notebook instance.

Notebook Instances Using OBS Storage
------------------------------------

For notebook instances that use OBS storage, you can use OBS or the ModelArts SDK to download files from OBS to a local PC.

-  Method 1: Downloading the files using OBS

   Download the files from OBS to a local path. If you have a large amount of data, use OBS Browser+ to download data or folders.

-  Method 2: Downloading the files using the ModelArts SDKs

   #. Download and install ModelArts SDKs in your local environment.

   #. Complete the session authentication of ModelArts SDKs.

   #. Download the files from OBS to a local path. The sample code is as follows:

      ::

         from modelarts.session import Session
         session=Session(access_key='***',secret_key='***',project_id='***',region_name='***')
         session.download_data(bucket_path="/bucket_name/obs_file.txt",path="/home/user/obs_file.txt")
