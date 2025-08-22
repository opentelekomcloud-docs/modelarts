:original_name: modelarts_13_0047.html

.. _modelarts_13_0047:

Failed to Publish a Dataset Version
===================================

If this fault occurs, the data does not meet the requirements of the data management module. As a result, the dataset fails to be published and the following operations cannot be performed.

Check your data, exclude the data that does not meet the following requirements, and restart the ExeML training task.

ModelArts.4710 OBS Permission Issues
------------------------------------

This fault is caused by OBS permissions when ModelArts interacts with OBS. If the message "OBS service Error Message" is displayed, the fault is caused by OBS permissions. Perform the following steps to rectify the fault. If this information is not contained in the error message, the fault is caused by backend services.

#. Check whether the current account has OBS permissions.

   Perform this step if you log in to ModelArts as an IAM user.

   Grant the current IAM user with the **Tenant Administrator** role whose **Scope** is **Global service project** so that the user has all OBS operation permissions. For details, see .

   To restrict the IAM user account' permissions, configure the minimum OBS operation permissions for it. For details, see .

#. Check whether the user has OBS bucket permissions.

   .. note::

      The OBS bucket described in the following steps is specified when you create an ExeML project or the one where the dataset selected during project creation is stored.

   -  Check whether the current account has been granted with the read and write permissions on the OBS bucket (specified in bucket ACLs).

      -  Go to the OBS management console, select the OBS bucket used by the ExeML project, and click the bucket name to go to the **Overview** page.
      -  In the left navigation pane, choose **Permissions** > **Bucket ACLs**. On the **Bucket ACLs** page that is displayed, check whether the current account has the read and write permissions. If it does not, contact the bucket owner to grant the permissions.

   -  Check whether the OBS bucket is unencrypted.

      a. Go to the OBS management console, select the OBS bucket used by the ExeML project, and click the bucket name to go to the **Overview** page.
      b. Ensure that the default encryption function is disabled for the OBS bucket. If the OBS bucket is encrypted, click **Default Encryption** and change its encryption status.

   -  Check whether the direct reading function of archived data is disabled.

      a. Go to the OBS management console, select the OBS bucket used by the ExeML project, and click the bucket name to go to the **Overview** page.
      b. Ensure that the direct reading function is disabled for the archived data in the OBS bucket. If this function is enabled, click **Direct Reading** and disable it.

ModelArts.4711 Number of Labeled Samples in the Dataset Does Not Meet Algorithm Requirements
--------------------------------------------------------------------------------------------

Each labeling type must contain at least five images.

ModelArts.4342 Labeling Information Does Not Meet Splitting Conditions
----------------------------------------------------------------------

If this fault occurs, modify the labeling data based on the following suggestions and try again.

-  At least two multi-label samples (that is, an image contains multiple labels) are required. If you enable dataset splitting when starting training and the number of images with multiple labels is less than 2, the dataset splitting fails. Check your labeling information and ensure that more than two images with multiple labels are labeled.
-  After the dataset is split, the label classes contained in the training set and validation set are different. Cause: In the multi-label scenario, after random data segmentation, samples containing a certain type of labels are classified into the training set. As a result, the verification set does not contain the label samples. This issue rarely occurs. You can try to release a new version to handle the issue.

ModelArts.4371 Dataset Version Already Exists
---------------------------------------------

If this error code is displayed, the dataset version already exists. In this case, republish the dataset version.

ModelArts.4712 Datasets Are Being Imported or Synchronized
----------------------------------------------------------

If the dataset used in ExeML is being imported or synchronized, this error occurs during training. In this case, start the ExeML training task after other tasks are complete.
