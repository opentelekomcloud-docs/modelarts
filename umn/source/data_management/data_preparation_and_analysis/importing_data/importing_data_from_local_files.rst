:original_name: dataprepare-modelarts-0019.html

.. _dataprepare-modelarts-0019:

Importing Data from Local Files
===============================

Prerequisites
-------------

-  You have created a dataset.
-  You have created an OBS bucket. The OBS bucket and ModelArts are in the same region and you can operate the bucket.

Import Operation
----------------

Both file and table data can be uploaded from local files. The data uploaded from local files should be stored in an OBS directory. You must have created an OBS bucket.

In a single batch upload, a maximum of 100 files can be uploaded at a time, and the total size of the files cannot exceed 5 GB.

The parameters on the GUI for data import vary according to the dataset type. The following uses a dataset of the image classification type as an example.

#. Log in to the ModelArts management console. In the navigation pane on the left, choose **Data Management** > **Datasets**.

#. Locate the row that contains the desired dataset and click **Import** in the **Operation** column.

   Alternatively, you can click the dataset name to go to the **Dashboard** tab of the dataset, and click **Import** in the upper right corner.

#. In the **Import** dialog box, set the parameters as follows and click **OK**.

   -  **Data Source**: **Local file**
   -  **Storage Path**: Select an OBS path.
   -  **Uploading Data**: Click **Upload data**, upload local data, and click **OK**.
