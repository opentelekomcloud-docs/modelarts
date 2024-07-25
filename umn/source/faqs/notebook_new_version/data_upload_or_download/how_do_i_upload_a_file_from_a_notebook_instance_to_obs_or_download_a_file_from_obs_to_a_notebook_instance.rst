:original_name: modelarts_05_0024.html

.. _modelarts_05_0024:

How Do I Upload a File from a Notebook Instance to OBS or Download a File from OBS to a Notebook Instance?
==========================================================================================================

In a notebook instance, you can call the ModelArts MoXing API or SDK to exchange data with OBS for uploading a file to OBS or downloading a file from OBS to the notebook instance.


.. figure:: /_static/images/en-us_image_0000001943979185.png
   :alt: **Figure 1** Uploading or downloading a file

   **Figure 1** Uploading or downloading a file

Method 1: Using MoXing to Upload and Download a File
----------------------------------------------------

Developed by the ModelArts team, MoXing is a distributed training acceleration framework built on open-source deep learning engines such as TensorFlow and PyTorch. MoXing makes model coding easier and more efficient.

MoXing provides a set of file object APIs for reading and writing OBS files.

Sample code:

.. code-block::

   import moxing as mox

   # Download the OBS folder sub_dir_0 from OBS to a notebook instance.
   mox.file.copy_parallel('obs://bucket_name/sub_dir_0', '/home/ma-user/work/sub_dir_0')
   # Download the OBS file obs_file.txt from OBS to a notebook instance.
   mox.file.copy('obs://bucket_name/obs_file.txt', '/home/ma-user/work/obs_file.txt')

   # Upload the OBS folder sub_dir_0 from a notebook instance to OBS.
   mox.file.copy_parallel('/home/ma-user/work/sub_dir_0', 'obs://bucket_name/sub_dir_0')
   # Upload the OBS file obs_file.txt from a notebook instance to OBS.
   mox.file.copy('/home/ma-user/work/obs_file.txt', 'obs://bucket_name/obs_file.txt')

Method 2: Using SDK to Upload and Download a File
-------------------------------------------------

Call the ModelArts SDK for downloading a file from OBS.

Sample code: Download **file1.txt** from OBS to **/home/ma-user/work/** in the notebook instance. All the bucket name, folder name, and file name are customizable.

::

   from modelarts.session import Session
   session = Session()
   session.obs.download_file(src_obs_file="obs://bucket-name/dir1/file1.txt", dst_local_dir="/home/ma-user/work/")

Call the ModelArts SDK for downloading a folder from OBS.

Sample code: Download **dir1** from OBS to **/home/ma-user/work/** in the notebook instance. The bucket name and folder name are customizable.

.. code-block::

   from modelarts.session import Session
   session = Session()
   session.obs.download_dir(src_obs_dir="obs://bucket-name/dir1/", dst_local_dir="/home/ma-user/work/")

Call the ModelArts SDK for uploading a file to OBS.

Sample code: Upload **file1.txt** in the notebook instance to OBS bucket **obs://bucket-name/dir1/**. All the bucket name, folder name, and file name are customizable.

::

   from modelarts.session import Session
   session = Session()
   session.obs.upload_file(src_local_file='/home/ma-user/work/file1.txt', dst_obs_dir='obs://bucket-name/dir1/')

Call the ModelArts SDK for uploading a folder to OBS.

Sample code: Upload **/work/** in the notebook instance to **obs://bucket-name/dir1/work/** of **bucket-name**. The bucket name and folder name are customizable.

.. code-block::

   from modelarts.session import Session
   session = Session()
   session.obs.upload_dir(src_local_dir='/home/ma-user/work/', dst_obs_dir='obs://bucket-name/dir1/')
