:original_name: datalabel-modelarts_0006.html

.. _datalabel-modelarts_0006:

Image Classification
====================

Training a model uses a large number of labeled images. Therefore, label images before the model training. You can add labels to images by manual labeling or auto labeling. In addition, you can modify the labels of images, or remove their labels and label the images again.

Before labeling an image in image classification scenarios, pay attention to the following:

-  You can add multiple labels to an image.
-  A label name can contain a maximum of 1,024 characters, including letters, digits, hyphens (-), and underscores (_).

Starting Labeling
-----------------

#. Log in to the ModelArts management console. In the navigation pane on the left, choose **Data Management** > **Label Data**.
#. On the right of the labeling job list, select a labeling type from the job type drop-down list. Click the job to be performed based on the labeling type. The details page of the job is displayed.
#. The job details page displays all data of the labeling job.

Synchronizing New Data
----------------------

ModelArts automatically synchronizes data and labeling information from datasets to the labeling job.

To quickly obtain the latest data in a dataset, in the **All statuses**, **Unlabeled**, or **Labeled** tab of the labeling job details page, click **Synchronize New Data**.

Filtering Data
--------------

In the **All statuses**, **Unlabeled**, or tab, click |image1| in the filter criteria area and add filter criteria to quickly filter the data you want to view.

The following filter criteria are available. You can set one or more filter criteria.

-  **Example Type**: Select **Hard example** or **Non-hard example**.
-  **Label**: Select **All** or one or more labels you specified.
-  **File Name** or **Path**: Filter files by file name or file storage path.
-  **Labeled By**: Select the name of the user who labeled the image.

Manually Labeling Images
------------------------

The labeling job details page displays the **All statuses**, **Unlabeled**, and **Labeled** tabs. The **Unlabeled** tab is displayed by default. Click an image to preview it. For the images that have been labeled, the label information is displayed at the bottom of the preview page.

#. In the **Unlabeled** tab, select the images to be labeled.

   -  Manual selection: In the image list, click the selection box in the upper left corner of an image to enter the selection mode, indicating that the image is selected. You can select multiple images of the same type and add labels to them together.
   -  Batch selection: If all the images on the current page of the image list belong to the same type, you can click **Select Images on Current Page** in the upper right corner to select all the images on the current page.

#. Add labels to the selected images.

   a. In the label adding area on the right, set a label in the **Label** text box.

      Click the **Label** text box and select an existing label from the drop-down list. If the existing labels cannot meet the requirements, input a label in the text box.

   b. Click **OK**. The selected images are automatically moved to the **Labeled** tab. In the **Unlabeled** and **All statuses** tabs, the labeling information is updated along with the labeling process, including the added label names and the number of images for each label.

   .. note::

      For details about how to label data, see **Labeling Description** on the dataset details page.

      a. Log in to the ModelArts management console. In the navigation pane on the left, choose **Data Management** > **Label Data**. The **Data Labeling** page is displayed.
      b. In the **My Creations** or **My Participations** tab, find the dataset to be labeled.
      c. Click the dataset name. The labeling details page is displayed. (By default, the **Unlabeled** tab is displayed.)
      d. In the upper right corner of the labeling details page, click **Labeling Description**.

Viewing Labeled Images
----------------------

On the labeling job details page, click the **Labeled** tab to view the list of labeled images. By default, the corresponding labels are displayed under the image thumbnails. You can also select an image and view the label information of the image in the **Labels of Selected Images** area on the right.

Modifying Labeled Data
----------------------

After labeling data, you can modify labeled data in the **Labeled** tab.

-  **Modifying based on images**

   On the labeling job details page, click the **Labeled** tab, and select one or more images to be modified from the image list. Modify the image information in the label information area on the right.

   Modifying a label: In the **Labels of Selected Images** area, click the edit icon in the **Operation** column, enter the correct label name in the text box, and click the check mark to complete the modification.

   Deleting a label: In the **Labels of Selected Images** area, click the delete icon in the **Operation** column to delete the label. This operation deletes only the labels added to the selected image.

-  **Modifying based on labels**

   -  On the labeling job details page, click **Label Management**. All labels are displayed on the list.

      -  Modifying a label: Click **Modify** in the **Operation** column. In the displayed dialog box, enter the new label name and click **OK**. After the modification, the images with the label added will use the new label name.
      -  Deleting a label: Click **Delete** in the **Operation** column to delete the label from all images that have been added with the label.

   -  Locate the target labeling job and click **Label** in the **Operation** column to go to the label management page.

      -  Click **Modify** in the **Operation** column of the target label to modify it.
      -  Click **Delete** in the **Operation** column of the target label to delete it.

Adding Data
-----------

In addition to the data automatically synchronized from datasets, you can directly add images to labeling jobs for labeling. The added data is first imported to the dataset associated with the labeling job. Then, the labeling job automatically synchronizes the latest data from the dataset.

#. On the labeling job details page, click **All statuses**, **Labeled**, or **Unlabeled** tab, click **Add data** in the upper left corner.

#. Configure the data source, import mode, import path, and labeling status.

#. Click **OK**.

   The images you have added will be automatically displayed in the image list in the **All statuses** tab. You can choose **Add data** > **View historical records** to view task history.

Deleting Images
---------------

You can quickly delete the images you want to discard.

In the **All statuses**, **Unlabeled**, or **Labeled** tab, select the images to be deleted or click **Select Images on Current Page**, and click **Delete**. In the displayed dialog box, select or deselect **Delete the source files from OBS** as required. After confirmation, click **Yes** to delete the images.

If a tick is displayed in the upper left corner of an image, the image is selected. If no image is selected on the page, the **Delete** button is unavailable.

.. note::

   If you select **Delete the source files from OBS**, images stored in the OBS directory will be deleted accordingly. This operation may affect other dataset versions or datasets using those files, for example, leading to an error in page display, training, or inference. Deleted data cannot be recovered. Exercise caution when performing this operation.

Managing Annotators
-------------------

If team labeling is enabled for a labeling job, view its labeling details in the **Annotator Management** tab. Additionally, you can add, modify, or delete annotators.

#. Choose **Data Management** > **Label Data**. In the **My Creations** or **My Participations** tab, view the list of all labeling jobs.
#. Locate the target team labeling job. (The name of a team labeling job is followed by |image2|.)
#. Choose **More** > **Annotator Management** in the **Operation** column. Alternatively, click the job name to go to the job details page, and choose **Team Labeling** > **Annotator Management** in the upper right corner.

-  Adding an annotator

   Click **Add Member**, select a member name, and click **OK**.

   Click **Send Email** in the **Operation** column to send the labeling job to the annotator by email.

-  Modifying annotator information

   Click **Modify** in the **Operation** column to modify the role of the annotator.

-  Deleting an annotator

   Click **Delete** in the **Operation** column to delete the annotator.

.. |image1| image:: /_static/images/en-us_image_0000002079101761.png
.. |image2| image:: /_static/images/en-us_image_0000002079101757.png
