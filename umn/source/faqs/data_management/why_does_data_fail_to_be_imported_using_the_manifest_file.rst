.. _modelarts_05_0103:

Why Does Data Fail to Be Imported Using the Manifest File?
==========================================================

Symptom
-------

Failed to use the manifest file of the published dataset to import data again.

Possible Cause
--------------

Data has been changed in the OBS directory of the published dataset, for example, images have been deleted. Therefore, the manifest file is inconsistent with data in the OBS directory. As a result, an error occurs when the manifest file is used to import data again.

Solution
--------

-  Method 1 (recommended): Publish a new version of the dataset again and use the new manifest file to import data.
-  Method 2: Modify the manifest file on your local PC, search for data changes in the OBS directory, and modify the manifest file accordingly. Ensure that the manifest file is consistent with data in the OBS directory, and then import data using the new manifest file.
