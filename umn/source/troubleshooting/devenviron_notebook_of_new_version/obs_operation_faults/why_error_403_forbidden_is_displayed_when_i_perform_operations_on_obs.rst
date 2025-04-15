:original_name: modelarts_13_0101.html

.. _modelarts_13_0101:

Why Error: 403 Forbidden Is Displayed When I Perform Operations on OBS?
=======================================================================

Symptom
-------

Message "Error: stat:403" is displayed when I use mox.file.copy_parallel in ModelArts to perform operations on OBS.


.. figure:: /_static/images/en-us_image_0000002233899768.png
   :alt: **Figure 1** Error message

   **Figure 1** Error message

Possible Causes
---------------

-  ModelArts uses an AK/SK for authentication globally, and the AK/SK has been deleted and recreated.
-  You do not have the permission to access OBS buckets.
-  The OBS bucket policy is incorrect.

Solution
--------

If you access the OBS bucket using an IAM user account, contact the tenant account to perform the following operations:

-  For cause 1, go to the global configuration page and reconfigure the authorization.
-  For cause 2, log in to the OBS console, search for the target OBS bucket, and click the bucket name to go to the **Overview** page. In the left navigation pane, choose **Permissions** > **Bucket ACLs**. On the **Bucket ACLs** page that is displayed, check whether the current account has the read and write permissions. If it does not, contact the bucket owner to grant the permissions.
-  For cause 2, log in to the OBS console, search for the target OBS bucket, and click the bucket name to go to the **Overview** page. In the navigation pane, choose **Permissions** > **Bucket Policy** and verify that the current OBS bucket can be accessed by IAM users.
