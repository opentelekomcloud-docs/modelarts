:original_name: modelarts_05_0193.html

.. _modelarts_05_0193:

Where Are Labeling Results Stored?
==================================

The ModelArts console provides data visualization capabilities, which allows you to view detailed data and labeling information on the console. To learn more about the path for storing labeling results, see the following description.

Context
-------

When creating a dataset in ModelArts, set both **Input Dataset Path** and **Output Dataset Path** to OBS.

-  **Input Dataset Path**: OBS path where the raw data is stored.
-  **Output Dataset Path**: Under this path, directories are generated based on the dataset version after data is labeled in ModelArts and datasets are published. The manifest files (containing data and labeling information) used in ModelArts are also stored in this path.

Procedure
---------

#. Log in to the ModelArts management console and choose **Data Management** > **Datasets**.
#. Locate the target dataset and click the triangle icon on the left of the dataset name to expand the dataset details. You can obtain the OBS path set for **Output Dataset Path**.

   .. note::

      Before obtaining labeling results, ensure that at least one dataset version is available.

#. Log in to the OBS management console and locate the version directory from the obtained OBS path to obtain the labeling result of the dataset.
