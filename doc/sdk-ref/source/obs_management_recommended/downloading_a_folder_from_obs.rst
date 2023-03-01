:original_name: modelarts_04_0221.html

.. _modelarts_04_0221:

Downloading a Folder from OBS
=============================

.. note::

   If the size of a file in a folder exceeds 5 GB, the file cannot be downloaded in this mode. However, other files whose size is less than 5 GB in the folder can be downloaded.

Sample Code
-----------

In the ModelArts notebook instance, you do not need to enter authentication parameters for session authentication. For details about session authentication of other development environments, see :ref:`Session Authentication <modelarts_04_0153>`.

::

   from modelarts.session import Session
   session = Session()
   session.obs.download_dir(src_obs_dir="obs://bucket-name/dir1/", dst_local_dir="/home/ma-user/work/")

After the sample code is executed, source folder **dir1** is downloaded from OBS to **/home/ma-user/work/dir1/**.

.. caution::

   You must have the write permission on the local path.

Parameter Description
---------------------

.. table:: **Table 1** Request parameters

   +---------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter     | Mandatory | Type   | Description                                                                                                                                                                                                                       |
   +===============+===========+========+===================================================================================================================================================================================================================================+
   | session       | Yes       | Object | Session object                                                                                                                                                                                                                    |
   +---------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | src_obs_dir   | Yes       | String | Path to the source folder to be downloaded from OBS. The path must start with **obs://** and end with a slash (/). If the downloaded folder contains empty folders, no empty folders are created in the corresponding local path. |
   +---------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dst_local_dir | Yes       | String | Path to the target local folder. The path must end with a slash (/).                                                                                                                                                              |
   +---------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Failed response parameters

   +-----------------------+-----------------------+------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                |
   +=======================+=======================+============================================================+
   | error_code            | String                | Error code when the API call fails.                        |
   |                       |                       |                                                            |
   |                       |                       | This parameter is not included when the API call succeeds. |
   +-----------------------+-----------------------+------------------------------------------------------------+
   | error_msg             | String                | Error message when the API call fails.                     |
   |                       |                       |                                                            |
   |                       |                       | This parameter is not included when the API call succeeds. |
   +-----------------------+-----------------------+------------------------------------------------------------+
