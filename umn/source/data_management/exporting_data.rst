.. _modelarts_23_0214:

Exporting Data
==============

A dataset includes labeled and unlabeled data. You can select images or filter data based on the filter criteria and export to a new dataset or the specified OBS directory. In addition, you can view the task history to learn about the export records.

.. note::

   Only datasets of image classification, object detection, image segmentation, and free format types can be exported.

   -  For image classification datasets, only the label files in TXT format can be exported.
   -  For object detection datasets, only XML label files in Pascal VOC format can be exported.
   -  For image segmentation datasets, only XML label files in Pascal VOC format and mask images can be exported.
   -  For free format datasets, all files of the datasets can be exported.

Exporting Data to a New Dataset
-------------------------------

#. Log in to the ModelArts management console. In the left navigation pane, choose **Data Management** > **Datasets**. The **Datasets** page is displayed.

#. In the dataset list, select the dataset of the object detection or image classification type and click the dataset name to go to the **Dashboard** tab page of the dataset.

   .. note::

      For a dataset of the free format type, you can click the dataset name to directly access the dataset details page and go to :ref:`4 <modelarts_23_0214__en-us_topic_0209632492_li114071010139>`.

#. On the **Dashboard** page of the dataset, click **Label** in the upper right corner. The dataset details page is displayed.

#. .. _modelarts_23_0214__en-us_topic_0209632492_li114071010139:

   On the dataset details page, select or filter data to be exported. Click **Export To** and choose **New Dataset** from the drop-down list.

#. In the displayed **Export to New Dataset** dialog box, enter the related information and click **OK**.

   **Name**: name of the new dataset

   **Storage Path**: input path of the new dataset, that is, the OBS path where the data to be exported is stored

   **Output Path**: output path of the new dataset, that is, the output path after labeling is complete. The output path cannot be the same as the storage path, and the output path cannot be a subdirectory of the storage path.

   **Export Content**: The options are **Export the selected samples** and **Export all samples meeting filtering criteria**.

#. After the data is exported, you can view the new dataset in the dataset list.

Exporting Data to OBS
---------------------

#. Log in to the ModelArts management console. In the left navigation pane, choose **Data Management** > **Datasets**. The **Datasets** page is displayed.

#. In the dataset list, select the dataset of the object detection or image classification type and click the dataset name to go to the **Dashboard** tab page of the dataset.

   .. note::

      For a dataset of the free format type, you can click the dataset name to directly access the dataset details page and go to :ref:`4 <modelarts_23_0214__en-us_topic_0209632492_li2056103713438>`.

#. On the **Dashboard** page of the dataset, click **Label** in the upper right corner. The dataset details page is displayed.

#. .. _modelarts_23_0214__en-us_topic_0209632492_li2056103713438:

   On the dataset details page, select or filter data to be exported. Click **Export To** and choose **OBS** from the drop-down list.

#. In the displayed **Export to OBS** dialog box, enter the related information and click **OK**.

   **Storage Path**: path where the data to be exported is stored. You are advised not to save data to the input or output path of the current dataset.

   **Export Content**: The options are **Export the selected samples** and **Export all samples meeting filtering criteria**.

#. After the data is exported, you can view it in the specified path.

Viewing the Task History
------------------------

When you export data to a new dataset or OBS, you can view the export task details in the **View Task History** dialog box.

#. Log in to the ModelArts management console. In the left navigation pane, choose **Data Management** > **Datasets**. The **Datasets** page is displayed.

#. In the dataset list, select the dataset of the object detection or image classification type and click the dataset name to go to the **Dashboard** tab page of the dataset.

   .. note::

      For a dataset of the free format type, you can click the dataset name to directly access the dataset details page and go to :ref:`4 <modelarts_23_0214__en-us_topic_0209632492_li19995141771413>`.

#. On the **Dashboard** page of the dataset, click **Label** in the upper right corner. The dataset details page is displayed.

#. .. _modelarts_23_0214__en-us_topic_0209632492_li19995141771413:

   On the dataset details page, select or filter data to be exported. Click **Export To** and choose **View Task History** from the drop-down list.

#. In the **View Task History** dialog box, view the export task history of the current dataset. Information about **Task ID**, **Created**, **Type**, **Path**, **Total**, and **Status** is included.
