:original_name: modelarts_04_0219.html

.. _modelarts_04_0219:

Uploading a Folder to OBS
=========================

Sample Code
-----------

In the ModelArts notebook instance, you do not need to enter authentication parameters for session authentication. For details about session authentication of other development environments, see :ref:`Session Authentication <modelarts_04_0153>`.

::

   from modelarts.session import Session
   session = Session()
   session.obs.upload_dir(src_local_dir='/home/ma-user/', dst_obs_dir='obs://bucket-name/dir1/')

After the sample code is executed, the local source folder **/ma-user/** is uploaded to the **dir1** folder in the **bucket-name** bucket. The path is **obs://bucket-name/dir1/ma-user/**. The bucket name and folder name are user-defined.

Parameter Description
---------------------

.. table:: **Table 1** Request parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                           |
   +=================+=================+=================+=======================================================================================================================================+
   | session         | Yes             | Object          | Session object                                                                                                                        |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | src_local_dir   | Yes             | String          | Path to the local folder to be uploaded.                                                                                              |
   |                 |                 |                 |                                                                                                                                       |
   |                 |                 |                 | If the folder to be uploaded is empty or contains multiple empty folders, no empty folders are created in the corresponding OBS path. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | dst_obs_dir     | Yes             | String          | Path to the target OBS bucket. The path must start with **obs://** and end with a slash (/).                                          |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------+

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
