:original_name: modelarts_30_0011.html

.. _modelarts_30_0011:

Downloading a File from JupyterLab to a Local Path
==================================================

Files created in JupyterLab can be downloaded to a local path. The operations for downloading a file are the same, regardless of whether the created notebook instance uses the default or EVS storage.

-  If a file is less than or equal to 100 MB, directly download it from JupyterLab. For details, see :ref:`Downloading a File Less Than or Equal to 100 MB <modelarts_30_0011__section2092816813316>`.
-  If a file is larger than 100 MB, use OBS to transfer it to your local path. For details, see :ref:`Downloading a File Larger Than 100 MB <modelarts_30_0011__section1343284817>`.

.. _modelarts_30_0011__section2092816813316:

Downloading a File Less Than or Equal to 100 MB
-----------------------------------------------

In the JupyterLab file list, right-click the file to be downloaded and choose **Download** from the shortcut menu. The file is downloaded to your browser's downloads folder.


.. figure:: /_static/images/en-us_image_0000001846057153.png
   :alt: **Figure 1** Downloading a file

   **Figure 1** Downloading a file

.. _modelarts_30_0011__section1343284817:

Downloading a File Larger Than 100 MB
-------------------------------------

Use OBS to transfer the file from the target notebook instance to the local path. To do so, perform the following operations:

#. In the notebook instance, create an IPYNB file larger than 100 MB and use MoXing to upload it to OBS. Example code is as follows:

   ::

      import moxing as mox
      mox.file.copy('/home/ma-user/work/obs_file.txt', 'obs://bucket_name/obs_file.txt')

   In the preceding code, **/home/ma-user/work/obs_file.txt** is the file storage path in the notebook instance, and **obs://bucket_name/obs_file.txt** is the file storage path in OBS.

#. Use OBS or ModelArts SDK to download the file from OBS to the local path.

   -  Method 1: Use OBS to download the file.
   -  Download **obs_file.txt** from OBS to the local path. If a large amount of data is to be downloaded, use OBS Browser+ to download.
   -  Method 2: Use ModelArts SDK to download the file.

      a. Download and install the SDK locally.

      b. Authenticate sessions.

      c. Download the file from OBS to the local path. Example code is as follows:

         ::

            from modelarts.session import Session
            session=Session(access_key='***',secret_key='***',project_id='***',region_name='***')
            session.download_data(bucket_path="/bucket_name/obs_file.txt",path="/home/user/obs_file.txt")
