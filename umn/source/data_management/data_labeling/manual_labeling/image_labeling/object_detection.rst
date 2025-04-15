:original_name: datalabel-modelarts_0007.html

.. _datalabel-modelarts_0007:

Object Detection
================

Training a model uses a large number of labeled images. Therefore, label images before the model training. You can add labels to images by manual labeling or auto labeling. In addition, you can modify the labels of images, or remove their labels and label the images again.

Before labeling an image in object detection scenarios, pay attention to the following:

-  All target objects in the image must be labeled.
-  Target objects are clear without any blocking and contained within bounding boxes.
-  Only the entire object must be contained within a bounding box. The edge of the bounding box cannot intersect the edge outline of the target object. Additionally, there must not be a gap between the edge and the target object to prevent the background from interfering with the model training.

Starting Labeling
-----------------

#. Log in to the ModelArts management console. In the navigation pane on the left, choose **Data Management** > **Label Data**.
#. In the labeling job list, select a labeling type from the **All type** drop-down list, click the job to be performed based on the labeling type. The details page of the job is displayed.
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

The labeling job details page displays the **All statuses**, **Unlabeled**, and **Labeled** tabs. The **Unlabeled** tab is displayed by default.

#. In the **Unlabeled** tab, click an image. The system automatically directs you to the page for labeling the image. For details about how to use common buttons on this page, see :ref:`Table 2 <en-us_topic_0000002268821389__en-us_topic_0000001185265231_table194471512463>`.

#. In the tool bar, select a proper labeling shape. The default labeling shape is a rectangle. In this example, the rectangle is used for labeling.

   .. note::

      In the tool bar, multiple tools are provided for you to label images. After you select a shape to label the first image, the shape automatically applies to subsequent images. You can switch the shape as required.

   .. table:: **Table 1** Supported bounding box

      +-----------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Icon      | Description                                                                                                                                                                                                                                                                                                                     |
      +===========+=================================================================================================================================================================================================================================================================================================================================+
      | |image8|  | Rectangle. You can also press **1**. Click the edge of the upper left corner of the object to be labeled. A rectangle will be displayed. Drag the rectangle to cover the object and click to label the object.                                                                                                                  |
      +-----------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | |image9|  | Polygon. You can also press **2**. In the area where the object to be labeled is located, click to label a point, move the mouse and click multiple points along the edge of the object, and then click the first point again. All the points form a polygon. In this way, the object to be labeled is within the bounding box. |
      +-----------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | |image10| | Round. You can also press **3**. Click the center point of an object, and move the mouse to draw a circle to cover the object and click to label the object.                                                                                                                                                                    |
      +-----------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | |image11| | Straight. You can also press **4**. Click to specify the start and end points of an object, and move the mouse to draw a straight line to cover the object and click to label the object.                                                                                                                                       |
      +-----------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | |image12| | Dashed line. You can also press **5**. Click to specify the start and end points of an object, and move the mouse to draw a dashed line to cover the object and click to label the object.                                                                                                                                      |
      +-----------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | |image13| | Dot. You can also press **6**. Click the object in an image to label a point.                                                                                                                                                                                                                                                   |
      +-----------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. In the **Add Label** text box, enter a new label name, select the label color, and click **Add**. Alternatively, select an existing label from the drop-down list.

   Label all objects in an image. Multiple labels can be added to an image. After labeling an image, click the right arrow (or press D) in the upper right corner of the image to switch to the next image and label the image.

#. Click **Back to Data Labeling Preview** in the upper left part of the page to view the labeling information. In the displayed dialog box, click **Yes** to save the labeling settings.

   The selected images are automatically moved to the **Labeled** tab. In the **Unlabeled** and **All statuses** tabs, the labeling information is updated along with the labeling process, including the added label names and the number of images for each label.

.. _en-us_topic_0000002268821389__en-us_topic_0000001185265231_table194471512463:

.. table:: **Table 2** Common icons on the labeling page

   +-----------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Icon      | Features                                                                                                                                                                           |
   +===========+====================================================================================================================================================================================+
   | |image22| | Cancel the previous operation. You can also press **Ctrl+Z**.                                                                                                                      |
   +-----------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | |image23| | Redo the previous operation. You can also press **Ctrl+Shift+Z**.                                                                                                                  |
   +-----------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | |image24| | Zoom in an image. You can also use the mouse wheel to zoom in.                                                                                                                     |
   +-----------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | |image25| | Zoom out an image. You can also use the mouse wheel to zoom out.                                                                                                                   |
   +-----------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | |image26| | Delete all bounding boxes on the current image. You can also press **Shift+Delete**.                                                                                               |
   +-----------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | |image27| | Show or hide a bounding box. This operation can be performed only on a labeled image. You can also press **Shift+H**.                                                              |
   +-----------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | |image28| | Drag a bounding box to another position or drag the edge of the bounding box to resize it. You can also use **X** + left mouse button.                                             |
   +-----------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | |image29| | Reset a bounding box. After dragging a bounding box, you can click this button to quickly restore the bounding box to its original shape and position. You can also press **Esc**. |
   +-----------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Viewing Labeled Images
----------------------

On the labeling job details page, click the **Labeled** tab to view the list of labeled images. The labels of each image are displayed below the image.

Quick Review
------------

Labeling jobs of the current object detection type cannot be reviewed in batches. If the label of a sample is modified or deleted, you need to go to the label details page to operate, which is complex. To simplify the operations, users can now review or modify labeling information in batches, improving efficiency.

#. Log in to the ModelArts management console. In the navigation pane, choose **Data Management** > **Label Data**. In the **My Creations** tab, select the target object detection labeling job from the **All types** drop-down list in the upper right corner.
#. In the labeling job list, click the target labeling job. The labeling details page is displayed.
#. Click **Quick Review** on the **Labeled** tab. On the displayed page, confirm the labeling results.
#. Batch review images of the same label.

   a. On the review page, select the label type from the drop-down list next to **Filter by Label**.
   b. Sort images of the selected label type by bounding box area or aspect ratio.
   c. Click an incorrectly labeled image, and then drag the labeling box to relabel the image. (**Modified** is displayed on the modified images.)
   d. You can select the incorrectly labeled images, and then click |image30| in the upper right corner to delete the label. (**Deleted** is displayed on the images whose label has been deleted.)
   e. You can also modify the label of a labeled image.

      #. Select the target images and click |image31| in the **All Labels** area on the right.
      #. Type a new label and click **OK**.

#. After the modification, click **Apply Modifications**. In the displayed dialog box, click **OK**. The system automatically returns to the labeling overview page and overwrites the original labeling data.
#. If you are not satisfied with the modified data, you can click **Cancel Modifications** to retain the original labeling data.

   .. table:: **Table 3** Buttons on the quick review page

      ========= ========================================
      Button    Features
      ========= ========================================
      |image32| Delete the label.
      |image33| Undo all operations on the current page.
      |image34| Undo the previous operation.
      |image35| Redo the previous operation.
      ========= ========================================

Modifying Labeled Data
----------------------

After labeling data, you can modify labeled data in the **Labeled** tab.

-  **Modifying based on images**

   On the labeling job details page, click the **Labeled** tab and then the image to be modified. The labeling page is displayed. Modify the image information in the label information area on the right.

   -  Modifying a label: In the **Labeling** area, click the edit icon, enter the correct label name in the text box, and click the check mark to complete the modification. Alternatively, click a label. In the image labeling area, adjust the position and size of the labeling box. After the adjustment, right-click the labeling box and choose **Modify** from the shortcut menu. Enter the new label and click **Modify** to save the modification.

   -  Deleting a label: In the **Labeling** area, click the deletion icon to delete a label from the image.

      After deleting the label, click **Back to Data Labeling Preview** in the upper left corner of the page to exit the labeling page. In the displayed dialog box, save the modification. After all labels of an image are deleted, the image is displayed in the **Unlabeled** tab.

-  **Modifying based on labels**

   -  On the labeling job details page, click **Label Management** on the right. All label information is displayed.

      -  Modifying a label: Click **Modify** in the **Operation** column. In the displayed dialog box, enter a new label name, select a new label color, and click **OK**. After the modification, the images with the label added will use the new label name.
      -  Deleting a label: Click **Delete** in the **Operation** column, or select the label to be deleted and click **Delete Label** above the label list.

   -  Alternatively, click **Label** in the **Operation** column of the target labeling job to go to the label management page.

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
#. Locate the target team labeling job. (The name of a team labeling job is followed by |image36|.)
#. Choose **More** > **Annotator Management** in the **Operation** column. Alternatively, click the job name to go to the job details page, and choose **Team Labeling** > **Annotator Management** in the upper right corner.

-  Adding an annotator

   Click **Add Member**, select a member name, and click **OK**.

   Click **Send Email** in the **Operation** column to send the labeling job to the annotator by email.

-  Modifying annotator information

   Click **Modify** in the **Operation** column to modify the role of the annotator.

-  Deleting an annotator

   Click **Delete** in the **Operation** column to delete the annotator.

.. |image1| image:: /_static/images/en-us_image_0000002268741685.png
.. |image2| image:: /_static/images/en-us_image_0000002268741665.png
.. |image3| image:: /_static/images/en-us_image_0000002268741725.png
.. |image4| image:: /_static/images/en-us_image_0000002233902284.png
.. |image5| image:: /_static/images/en-us_image_0000002268821617.png
.. |image6| image:: /_static/images/en-us_image_0000002268741701.png
.. |image7| image:: /_static/images/en-us_image_0000002268821501.png
.. |image8| image:: /_static/images/en-us_image_0000002268741665.png
.. |image9| image:: /_static/images/en-us_image_0000002268741725.png
.. |image10| image:: /_static/images/en-us_image_0000002233902284.png
.. |image11| image:: /_static/images/en-us_image_0000002268821617.png
.. |image12| image:: /_static/images/en-us_image_0000002268741701.png
.. |image13| image:: /_static/images/en-us_image_0000002268821501.png
.. |image14| image:: /_static/images/en-us_image_0000002268741621.png
.. |image15| image:: /_static/images/en-us_image_0000002268821609.png
.. |image16| image:: /_static/images/en-us_image_0000002233902208.png
.. |image17| image:: /_static/images/en-us_image_0000002233742424.png
.. |image18| image:: /_static/images/en-us_image_0000002268821573.png
.. |image19| image:: /_static/images/en-us_image_0000002233742348.png
.. |image20| image:: /_static/images/en-us_image_0000002268821601.png
.. |image21| image:: /_static/images/en-us_image_0000002268741569.png
.. |image22| image:: /_static/images/en-us_image_0000002268741621.png
.. |image23| image:: /_static/images/en-us_image_0000002268821609.png
.. |image24| image:: /_static/images/en-us_image_0000002233902208.png
.. |image25| image:: /_static/images/en-us_image_0000002233742424.png
.. |image26| image:: /_static/images/en-us_image_0000002268821573.png
.. |image27| image:: /_static/images/en-us_image_0000002233742348.png
.. |image28| image:: /_static/images/en-us_image_0000002268821601.png
.. |image29| image:: /_static/images/en-us_image_0000002268741569.png
.. |image30| image:: /_static/images/en-us_image_0000002233902180.png
.. |image31| image:: /_static/images/en-us_image_0000002268741705.png
.. |image32| image:: /_static/images/en-us_image_0000002233742320.png
.. |image33| image:: /_static/images/en-us_image_0000002233742296.png
.. |image34| image:: /_static/images/en-us_image_0000002268821585.png
.. |image35| image:: /_static/images/en-us_image_0000002268821545.png
.. |image36| image:: /_static/images/en-us_image_0000002233902152.png
