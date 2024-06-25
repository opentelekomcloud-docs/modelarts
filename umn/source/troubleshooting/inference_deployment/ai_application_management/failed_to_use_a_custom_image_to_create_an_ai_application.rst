:original_name: modelarts_13_0210.html

.. _modelarts_13_0210:

Failed to Use a Custom Image to Create an AI application
========================================================

Symptom
-------

When I used a custom image to create an AI application, the creation failed.

Possible Causes
---------------

Possible causes are as follows:

-  The URL of the image used for importing the AI application is invalid or the image is unavailable.
-  SWR operation permissions are not included in the agency authorization configured on ModelArts.
-  The IAM user does not obtain SWR operation permissions from the tenant.
-  The image used is from another account.
-  The image used is a public image.

Solution
--------

#. Go to the SWR console and check whether the target image is available and whether the URL of the image is the same as the actual one, including the spelling and letter cases in the URL.

#. Check whether SWR operation permissions are included in the agency authorization configured on ModelArts. To do so, go to the **Global Configuration** page on ModelArts and view the authorization details. If no SWR operation permissions are configured, go to the IAM console and grant the permissions to the target agency.

#. Set a private image

   Log in to SWR, choose **My Images** in the navigation pane on the left to view image details. Click **Edit** in the upper right corner and set **Type** to **Private**.
