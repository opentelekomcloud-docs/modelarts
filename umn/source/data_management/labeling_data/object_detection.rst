.. _modelarts_23_0012:

Object Detection
================

Model training uses a large number of labeled images. Therefore, before the model training, add labels to the images that are not labeled. You can add labels to images by manual labeling or auto labeling. In addition, you can modify the labels of images, or remove their labels and label the images again.

Before labeling an image in object detection scenarios, pay attention to the following:

-  All target objects in the image must be labeled.
-  Target objects are clear without any blocking and contained within bounding boxes.
-  Only the entire object must be contained within a bounding box. The edge of the bounding box cannot intersect the edge outline of the target object. Additionally, there must not be a gap between the edge and the target object to prevent the background from interfering with the model training.

Labeling the Dataset
--------------------

#. Log in to the ModelArts management console. In the left navigation pane, choose **Data Management** > **Datasets**. The **Datasets** page is displayed.

#. In the dataset list, click the dataset to be labeled based on the labeling type. The **Dashboard** tab page of the dataset is displayed.

   By default, the **Dashboard** tab page of the current dataset version is displayed. To label the dataset of another version, click the **Versions** tab and then click **Set to Current Version** in the right pane. For details, see :ref:`Managing Dataset Versions <modelarts_23_0019>`.

#. On the **Dashboard** page of the dataset, click **Label** in the upper right corner. The dataset details page is displayed. By default, all data of the dataset is displayed on the dataset details page.

Synchronizing Data Sources
--------------------------

ModelArts automatically synchronizes data and labeling information from **Input Dataset Path** to the dataset details page.

-  For an image classification dataset, the .txt file with the same name in the same directory as the data source is used as the label of the target image.
-  For an object detection dataset or image segmentation dataset, the .xml file with the same name in the same directory is used as the label of the target image.

To quickly obtain the latest data in the OBS bucket, on the **All** or **Unlabeled** tab page of the dataset details page, click **Synchronize Data Source**.

Filtering Data
--------------

On the **Dashboard** tab page of the dataset, the summary of the dataset is displayed by default. In the upper left corner of the page, click **Label**. The dataset details page is displayed, showing all data in the dataset by default. On the **All**, **Unlabeled**, or **Labeled** tab page, you can add filter criteria in the filter criteria area to quickly filter the data you want to view.

The following filter criteria are supported. You can set one or more filter criteria.

-  **Label**: Select **All** or one or more labels you specified.
-  **Sample Creation Time**: Select **Within 1 month**, **Within 1 day**, or **Custom** to customize a time range.
-  **File Name** or **Path**: Filter files by file name or file storage path.
-  **Labeled By**: Select the name of the user who performs the labeling operation.

.. _modelarts_23_0012__en-us_topic_0170889732_section888019266174:

Labeling Images (Manually)
--------------------------

The dataset details page provides the **Labeled** and **Unlabeled** tabs. The **All** tab page is displayed by default.

#. On the **Unlabeled** tab page, click an image. The image labeling page is displayed. For details about how to use common buttons on the **Labeled** tab page, see :ref:`Table 2 <modelarts_23_0012__en-us_topic_0170889732_table194471512463>`.

#. In the left tool bar, select a proper labeling shape. The default labeling shape is a rectangle. In this example, the rectangle is used for labeling.

   .. note::

      On the left of the page, multiple tools are provided for you to label images. However, you can use only one tool at a time.

   .. _modelarts_23_0012__en-us_topic_0170889732_table165201739119:

   .. table:: **Table 1** Supported bounding box

      +-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Icon      | Description                                                                                                                                                                                                                                                                                     |
      +===========+=================================================================================================================================================================================================================================================================================================+
      | |image7|  | Rectangle. Click the edge of the upper left corner of the object to be labeled. A rectangle will be displayed. Drag the rectangle to cover the object and click to label the object.                                                                                                            |
      +-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | |image8|  | Polygon. In the area where the object to be labeled is located, click to label a point, move the mouse and click multiple points along the edge of the object, and then click the first point again. All the points form a polygon. Therefore, the object to be labeled is in the bounding box. |
      +-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | |image9|  | Circle. Click the center point of an object, and move the mouse to draw a circle to cover the object and click to label the object.                                                                                                                                                             |
      +-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | |image10| | Straight line. Click to specify the start and end points of an object, and move the mouse to draw a straight line to cover the object and click to label the object.                                                                                                                            |
      +-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | |image11| | Dotted line. Click to specify the start and end points of an object, and move the mouse to draw a dotted line to cover the object and click to label the object.                                                                                                                                |
      +-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | |image12| | Point. Click the object in an image to label a point.                                                                                                                                                                                                                                           |
      +-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. In the **Add Label** text box, enter a new label name, select the label color, and click **Add**. Alternatively, select an existing label from the drop-down list.

   Label all objects in an image. Multiple labels can be added to an image. After labeling an image, you can click the image list below the image to quickly select other images that are not labeled and label them on the labeling page.

#. Click **Back to Data Labeling Preview** in the upper left part of the page to view the labeling information. In the dialog box that is displayed, click **OK** to save the labeling settings.

   The selected image is automatically moved to the **Labeled** tab page. On the **Unlabeled** and **All** tab pages, the labeling information is updated along with the labeling process, including the added label names and the number of images for each label.

.. _modelarts_23_0012__en-us_topic_0170889732_table194471512463:

.. table:: **Table 2** Common icons on the labeling page

   +-----------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | Icon      | Description                                                                                                                             |
   +===========+=========================================================================================================================================+
   | |image22| | Cancel the previous operation.                                                                                                          |
   +-----------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | |image23| | Redo the previous operation.                                                                                                            |
   +-----------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | |image24| | Zoom in an image.                                                                                                                       |
   +-----------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | |image25| | Zoom out an image.                                                                                                                      |
   +-----------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | |image26| | Delete all bounding boxes on the current image.                                                                                         |
   +-----------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | |image27| | Display or hide a bounding box. You can perform this operation only on a labeled image.                                                 |
   +-----------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | |image28| | Drag a bounding box to another position or drag the edge of the bounding box to resize it.                                              |
   +-----------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | |image29| | Reset. After dragging a bounding box, you can click this button to quickly restore the bounding box to its original shape and position. |
   +-----------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | |image30| | Display the labeled image in full screen.                                                                                               |
   +-----------+-----------------------------------------------------------------------------------------------------------------------------------------+

Viewing Labeled Images
----------------------

On the dataset details page, click the **Labeled** tab to view the list of the labeled images. You can click an image to view the label information about the image in the **All Labels** area on the right.

Modifying Labeling Information
------------------------------

After labeling data, you can modify labeled data on the **Labeled** tab page.

-  **Modifying based on images**

   On the dataset details page, click the **Labeled** tab, click the image to be modified. The labeling page is displayed. Modify the image information in the label information area on the right.

   -  Modifying a label: In the **Labeling** area, click the edit icon, enter the correct label name in the text box, and click the check mark to complete the modification. Alternatively, click a label. In the image labeling area, adjust the position and size of the bounding box. After the adjustment is complete, click another label to save the modification.

   -  Deleting a label: In the **Labeling** area, click the deletion icon to delete a label from the image.

      After deleting the label, click **Back to Data Labeling Preview** in the upper left corner of the page to exit the labeling page. In the dialog box that is displayed, save the modification. After all labels of an image are deleted, the image is displayed on the **Unlabeled** tab page.

      .. _modelarts_23_0012__en-us_topic_0170889732_en-us_topic_0170889732_fig16709173213107:

      .. figure:: /_static/images/en-us_image_0000001157080933.png
         :alt: **Figure 1** Editing an object detection label
      

         **Figure 1** Editing an object detection label

-  **Modifying based on labels**

   On the dataset details page, click the **Labeled** tab. The information about all labels is displayed on the right.

   -  Modifying a label: Click the edit icon in the **Operation** column. In the dialog box that is displayed, enter the new label name, select the new label color, and click **OK**. After the modification, the images that have been added with the label use the new label name.
   -  Deleting a label: Click the deletion icon in the **Operation** column to delete a label.

   .. _modelarts_23_0012__en-us_topic_0170889732_en-us_topic_0170889732_fig19495403277:

   .. figure:: /_static/images/en-us_image_0000001157080935.png
      :alt: **Figure 2** All labels for object detection
   

      **Figure 2** All labels for object detection

Adding Images
-------------

In addition to the data automatically synchronized from **Input Dataset Path**, you can directly add images on ModelArts for labeling.

#. On the dataset details page, click the **All** or **Unlabeled** tab. Then, click **Add**.

#. On the **Add** page that is displayed, click **Add Image**.

   Select one or more images to be uploaded in the local environment. Images in JPG, JPEG, PNG, or BMP formats are supported. The size of a single image cannot exceed 5 MB, and the total size of all images uploaded at a time cannot exceed 8 MB.

   After the images are selected, their thumbnails and total size are displayed on the **Add** page.

#. On the **Add** page, click **OK**.

   The images you have added will be automatically displayed in the image list on the **Unlabeled** tab page. In addition, the images are automatically saved to the OBS directory specified by **Input Dataset Path**.

Deleting Images
---------------

You can quickly delete the images you want to discard.

On the **All**, **Unlabeled**, or **Labeled** tab page, select the images to be deleted or click **Select Images on Current Page**, and click **Delete** in the upper left corner to delete them. In the displayed dialog box, select or deselect **Delete source files** as required. After confirmation, click **OK** to delete the images.

If a tick is displayed in the upper left corner of an image, the image is selected. If no image is selected on the page, the **Delete** button is unavailable.

.. note::

   If you select **Delete source files**, images stored in the OBS directory will be deleted accordingly. This operation may affect other dataset versions or datasets using those files, for example, leading to an error in page display, training, or inference. Deleted data cannot be recovered. Exercise caution when performing this operation.

.. |image1| image:: /_static/images/en-us_image_0000001156920971.png

.. |image2| image:: /_static/images/en-us_image_0000001156920969.png

.. |image3| image:: /_static/images/en-us_image_0000001157080923.png

.. |image4| image:: /_static/images/en-us_image_0000001110761098.png

.. |image5| image:: /_static/images/en-us_image_0000001110920992.png

.. |image6| image:: /_static/images/en-us_image_0000001110920994.png

.. |image7| image:: /_static/images/en-us_image_0000001156920971.png

.. |image8| image:: /_static/images/en-us_image_0000001156920969.png

.. |image9| image:: /_static/images/en-us_image_0000001157080923.png

.. |image10| image:: /_static/images/en-us_image_0000001110761098.png

.. |image11| image:: /_static/images/en-us_image_0000001110920992.png

.. |image12| image:: /_static/images/en-us_image_0000001110920994.png

.. |image13| image:: /_static/images/en-us_image_0000001110920996.png

.. |image14| image:: /_static/images/en-us_image_0000001110920984.png

.. |image15| image:: /_static/images/en-us_image_0000001110761082.png

.. |image16| image:: /_static/images/en-us_image_0000001110920982.png

.. |image17| image:: /_static/images/en-us_image_0000001156920959.png

.. |image18| image:: /_static/images/en-us_image_0000001110921000.png

.. |image19| image:: /_static/images/en-us_image_0000001110761080.png

.. |image20| image:: /_static/images/en-us_image_0000001110921004.png

.. |image21| image:: /_static/images/en-us_image_0000001110920978.png

.. |image22| image:: /_static/images/en-us_image_0000001110920996.png

.. |image23| image:: /_static/images/en-us_image_0000001110920984.png

.. |image24| image:: /_static/images/en-us_image_0000001110761082.png

.. |image25| image:: /_static/images/en-us_image_0000001110920982.png

.. |image26| image:: /_static/images/en-us_image_0000001156920959.png

.. |image27| image:: /_static/images/en-us_image_0000001110921000.png

.. |image28| image:: /_static/images/en-us_image_0000001110761080.png

.. |image29| image:: /_static/images/en-us_image_0000001110921004.png

.. |image30| image:: /_static/images/en-us_image_0000001110920978.png

