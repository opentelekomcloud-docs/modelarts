:original_name: dataprepare-modelarts-0032.html

.. _dataprepare-modelarts-0032:

Exporting Data to a New Dataset
===============================

#. Log in to the ModelArts management console. In the left navigation pane, choose **Data Management** > **Datasets**.

#. In the dataset list, select an image dataset and click the dataset name to go to the **Dashboard** tab page of the dataset.

#. Click **Export** in the upper right corner. In the displayed **Export To** dialog box, enter the related information and click **OK**.

   **Type**: **New Dataset**.

   **Name**: name of the new dataset

   **Storage Path**: input path of the new dataset, that is, the OBS path where the data to be exported is stored

   **Output Path**: output path of the new dataset, that is, the output path after labeling is complete The output path cannot be the same as the storage path, and the output path cannot be a subdirectory of the storage path.

#. After the data is exported, view it in the specified path. After the data is exported, you can view the new dataset in the dataset list.

#. On the **Dashboard** tab page, click **Export History** in the upper right corner. In the displayed dialog box, view the task history of the dataset.
