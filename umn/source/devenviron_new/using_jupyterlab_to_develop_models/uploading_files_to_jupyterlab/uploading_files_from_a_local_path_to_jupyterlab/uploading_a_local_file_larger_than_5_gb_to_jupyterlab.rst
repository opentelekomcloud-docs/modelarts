:original_name: modelarts_30_0047.html

.. _modelarts_30_0047:

Uploading a Local File Larger Than 5 GB to JupyterLab
=====================================================

A file exceeding 5 GB cannot be directly uploaded to JupyterLab.

To upload files exceeding 5 GB, upload them to OBS. Then, call the ModelArts MoXing or SDK API in the target notebook instance to read and write the files in OBS.


.. figure:: /_static/images/en-us_image_0000001846137341.png
   :alt: **Figure 1** Uploading and downloading large files in a notebook instance

   **Figure 1** Uploading and downloading large files in a notebook instance

The procedure is as follows:

#. Upload the file from a local path to OBS.
#. Download the file from OBS to the notebook instance by calling the ModelArts SDK or MoXing API.

   -  Method 1: Call the ModelArts SDK interconnected with the OBS API to download a file from OBS.

      Example code:

      ::

         from modelarts.session import Session
         session = Session()
         session.obs.copy("obs://bucket-name/obs_file.txt","/home/ma-user/work/")

   -  Method 2: Call the ModelArts MoXing API for reading an OBS file.

      .. code-block::

         import moxing as mox

         # Download the OBS folder sub_dir_0 from OBS to a notebook instance.
         mox.file.copy_parallel('obs://bucket_name/sub_dir_0', '/home/ma-user/work/sub_dir_0')
         # Download the OBS file obs_file.txt from OBS to a notebook instance.
         mox.file.copy('obs://bucket_name/obs_file.txt', '/home/ma-user/work/obs_file.txt')

      If a .zip file is downloaded, run the following command on the terminal to decompress the package:

      .. code-block::

         unzip xxx.zip  # Directly decompress the package in the path where the package is stored.

      After the code is executed, open the terminal shown in :ref:`Figure 2 <modelarts_30_0047__fig711883121018>` and run the **ls /home/ma-user/work** command to view the file downloaded to the notebook instance. Alternatively, view the downloaded file in the left navigation pane of Jupyter. If the file is not displayed, refresh the page.

      .. _modelarts_30_0047__fig711883121018:

      .. figure:: /_static/images/en-us_image_0000001846057261.png
         :alt: **Figure 2** Opening the terminal

         **Figure 2** Opening the terminal


      .. figure:: /_static/images/en-us_image_0000001846137357.png
         :alt: **Figure 3** File downloaded to a notebook instance

         **Figure 3** File downloaded to a notebook instance

Error Handling
--------------

If you download a file from OBS to your notebook instance and the system displays error message "Permission denied", perform the following operations for troubleshooting:

-  Ensure that the target OBS bucket and notebook instance are in the same region. If the OBS bucket and notebook instance are in different regions, the access to OBS is denied.
-  Ensure that the notebook account has the permission to read data in the OBS bucket.
