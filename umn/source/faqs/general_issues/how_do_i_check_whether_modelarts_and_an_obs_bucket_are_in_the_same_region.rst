:original_name: modelarts_05_0073.html

.. _modelarts_05_0073:

How Do I Check Whether ModelArts and an OBS Bucket Are in the Same Region?
==========================================================================

If an OBS directory needs to be specified for using ModelArts functions, such as creating training jobs and datasets, ensure that the OBS bucket and ModelArts are in the same region.

Checking Whether the OBS Bucket and ModelArts Are in the Same Region
--------------------------------------------------------------------

#. Check the region where the created OBS bucket resides.

   a. Log in to .

   b. On the **Object Storage Service** page, to search for a bucket, enter a keyword in **Bucket Name**.

      In the **Region** column, view the region where the created OBS bucket is located.

#. Check the region where ModelArts is deployed.

   Log in to the ModelArts console and view the region where ModelArts resides in the upper left corner.

#. Check whether the region of the created OBS bucket is the same as that of ModelArts. Ensure that the OBS bucket is in the same region as ModelArts.
