:original_name: modelarts_04_0220.html

.. _modelarts_04_0220:

Downloading a File from OBS
===========================

.. note::

   If the size of a file in a folder exceeds 5 GB, the file cannot be downloaded in this mode.

Sample Code
-----------

In the ModelArts notebook instance, you do not need to enter authentication parameters for session authentication. For details about session authentication of other development environments, see :ref:`Session Authentication <modelarts_04_0153>`.

::

   from modelarts.session import Session
   session = Session()
   session.obs.download_file(src_obs_file="obs://bucket-name/dir1/file1.txt", dst_local_dir="/home/ma-user/")

After the sample code is executed, source file **file1.txt** is downloaded from OBS to **/home/ma-user/file1.txt**.

Parameter Description
---------------------

.. table:: **Table 1** Request parameters

   +---------------+-----------+--------+-----------------------------------------------------------------------------------------+
   | Parameter     | Mandatory | Type   | Description                                                                             |
   +===============+===========+========+=========================================================================================+
   | session       | Yes       | Object | Session object                                                                          |
   +---------------+-----------+--------+-----------------------------------------------------------------------------------------+
   | src_obs_file  | Yes       | String | Path to the source file to be downloaded from OBS. The path must start with **obs://**. |
   +---------------+-----------+--------+-----------------------------------------------------------------------------------------+
   | dst_local_dir | Yes       | String | Path to the target local folder. The path must end with a slash (/).                    |
   +---------------+-----------+--------+-----------------------------------------------------------------------------------------+

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
