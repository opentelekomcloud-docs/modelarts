:original_name: modelarts_13_0157.html

.. _modelarts_13_0157:

Incorrect OBS Path on ModelArts
===============================

Symptom
-------

When ModelArts attempts to use an OBS bucket path, a message is displayed, indicating that the created OBS bucket is unavailable.

Alternatively, error message "ModelArts.2791: Invalid OBS path" is displayed.

Possible Causes
---------------

-  Access authorization has not been configured on ModelArts.
-  Encrypted files are to upload to OBS. ModelArts does not support encrypted OBS files.
-  The permissions and access control lists (ACLs) of the OBS bucket are incorrectly configured.
-  When a training job is created, the code directory and boot file are configured incorrectly.

Solution
--------

**Configure access authorization.**

For details, see "Configuring Access Authorization (Global Configuration)".

**Check whether the OBS bucket is encrypted.**

#. Log in to the OBS management console and click the bucket name to go to the **Overview** page.
#. Ensure that default encryption is disabled for the OBS bucket. If the OBS bucket is encrypted, click **Default Encryption** and disable it.

**Check whether the OBS file is encrypted.**

#. Log in to the OBS management console and click the bucket name to go to the **Overview** page.
#. In the navigation pane on the left, choose **Objects**. The object list is displayed. Click the name of the object that stores files and find the target file. In the file list, check whether the file is encrypted. File encryption cannot be canceled. In this case, cancel bucket encryption and upload images or files again.

**Check the ACLs of the OBS bucket.**

#. Log in to the OBS management console and click the bucket name to go to the **Overview** page.
#. In the navigation pane on the left, choose **Permissions** > **Bucket ACLs**. On the **Bucket ACLs** page, check whether the current account has the read and write permissions to the bucket. If it does not, contact the bucket owner to grant the permissions.

**Check the code directory and boot file of a training job.**

#. Log in to the ModelArts management console, choose **Training Management** > **Training Jobs**, locate the failed training job, and click its name or ID to go to the job details page.
#. In the left pane of the details page, check whether the code directory and boot file are correctly selected.

   -  Select an OBS directory for code directory. If a file is selected, the system will display a message indicating an invalid OBS path.
   -  The boot file must be in the .py format. Otherwise, the system will display a message indicating an invalid OBS path.
