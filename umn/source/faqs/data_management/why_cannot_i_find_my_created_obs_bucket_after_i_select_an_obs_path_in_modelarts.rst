:original_name: modelarts_05_0509.html

.. _modelarts_05_0509:

Why Cannot I Find My Created OBS Bucket After I Select an OBS Path in ModelArts?
================================================================================

Verify that your created bucket and ModelArts are in the same region.

#. Check the region where the created OBS bucket is located.

   a. Log in to the .

   b. On the **Object Storage Service** page, locate the destination bucket by name, or enter a keyword in the search box and search for it.

      In the **Region** column, view the region where the created OBS bucket is located.

#. Check the region where ModelArts is deployed.

   Log in to the ModelArts management console and view the region where ModelArts is located in the upper left corner.

#. Check whether the region of the created OBS bucket is the same as that of ModelArts. Ensure that they are the same.
