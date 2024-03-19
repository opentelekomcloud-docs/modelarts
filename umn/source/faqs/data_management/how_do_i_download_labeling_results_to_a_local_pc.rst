:original_name: modelarts_05_0194.html

.. _modelarts_05_0194:

How Do I Download Labeling Results to a Local PC?
=================================================

After being published, the labeling information and data in ModelArts datasets are stored as manifest files in the OBS path set for **Output Dataset Path**.

To obtain the OBS path, do as follows:

#. Log in to the ModelArts management console and choose **Data Management** > **Datasets**.
#. Locate the target dataset and click the triangle icon on the left of the dataset name to expand the dataset details. You can obtain the OBS path set for **Output Dataset Path**.
#. Log in to the OBS management console and locate the version directory from the obtained OBS path to obtain the labeling result of the dataset.

To download the labeling results to a local PC, go to the OBS path where the manifest files are stored and click **Download**.
