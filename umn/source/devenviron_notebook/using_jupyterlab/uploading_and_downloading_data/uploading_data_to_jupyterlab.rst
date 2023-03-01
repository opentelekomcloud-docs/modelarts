:original_name: modelarts_23_0332.html

.. _modelarts_23_0332:

Uploading Data to JupyterLab
============================

On the **JupyterLab** page, click **Upload Files** to upload a file. For details, see :ref:`Uploading a File <modelarts_23_0209__en-us_topic_0208766071_section172463910383>` in :ref:`Introduction to JupyterLab and Common Operations <modelarts_23_0209>`. If a message is displayed indicating that the size of the files to be uploaded exceeds the upper limit when uploading files to notebook instances or JupyterLab, you can upload the files to OBS and then download them to notebook instances.

Step 1: Uploading Files to OBS
------------------------------

Use the OBS API to upload large files because OBS Console has restrictions on the file size and quantity.

Step 2: Downloading Files from OBS to Notebook Instances
--------------------------------------------------------

A notebook instance can be mounted to OBS as the storage location. The operation method varies depending on the instance types.

-  Downloading files to notebook instances using OBS for data storage

   Upload files to the OBS path specified during notebook instance creation and synchronize the files from OBS to the notebook instances using Sync OBS.
