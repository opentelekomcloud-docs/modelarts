:original_name: modelarts_04_0218.html

.. _modelarts_04_0218:

Uploading a File to OBS
=======================

Sample Code
-----------

In the ModelArts notebook instance, you do not need to enter authentication parameters for session authentication. For details about session authentication of other development environments, see :ref:`Session Authentication <modelarts_04_0153>`.

::

   from modelarts.session import Session
   session = Session()
   session.obs.upload_file(src_local_file='/home/ma-user/file1.txt', dst_obs_dir='obs://bucket-name/dir1/')

After the sample code is executed, the local source file **file1.txt** is uploaded to the **dir1** folder in the **bucket-name** bucket. The path is **obs://bucket-name/dir1/file1.txt**. The bucket name and folder name are user-defined.

Parameter Description
---------------------

.. table:: **Table 1** Request parameters

   +----------------+-----------+--------+----------------------------------------------------------------------------------------------+
   | Parameter      | Mandatory | Type   | Description                                                                                  |
   +================+===========+========+==============================================================================================+
   | session        | Yes       | Object | Session object                                                                               |
   +----------------+-----------+--------+----------------------------------------------------------------------------------------------+
   | src_local_file | Yes       | String | Path to the local file to be uploaded                                                        |
   +----------------+-----------+--------+----------------------------------------------------------------------------------------------+
   | dst_obs_dir    | Yes       | String | Path to the target OBS bucket. The path must start with **obs://** and end with a slash (/). |
   +----------------+-----------+--------+----------------------------------------------------------------------------------------------+

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
