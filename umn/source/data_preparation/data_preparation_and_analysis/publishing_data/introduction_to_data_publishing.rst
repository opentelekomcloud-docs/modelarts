:original_name: dataprepare-modelarts-0027.html

.. _dataprepare-modelarts-0027:

Introduction to Data Publishing
===============================

ModelArts distinguishes data of the same source according to versions processed or labeled at different time, which facilitates the selection of dataset versions for subsequent model building and development.

About Dataset Versions
----------------------

-  For a newly created dataset (before publishing), there is no dataset version information. The dataset must be published before being used for model development or training.
-  The default naming rules of dataset versions are V001 and V002 in ascending order. You can customize the version number during publishing.
-  You can set any version to the current version. Then the details of the version are displayed on the dataset details page.
-  You can obtain the dataset in the manifest file format corresponding to each dataset version based on the value of **Storage Path**. The dataset can be used when you import data or filter hard examples.
-  The version of a table dataset cannot be changed.
