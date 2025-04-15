:original_name: datalabel-modelarts_0008.html

.. _datalabel-modelarts_0008:

Image Segmentation
==================

Training a model uses a large number of labeled images. Therefore, label images before the model training. You can label images on the ModelArts management console. Alternatively, modify labels, or delete them and label them again.

Before labeling an image in image segmentation scenarios, pay attention to the following:

-  All objects whose contours need to be extracted from the image must be labeled.
-  Polygons can be used for labeling.

   -  In polygon labeling, draw a polygon based on the outline of the target object.

-  When labeling an image, ensure that the polygons are within the image. Otherwise, an error will occur in subsequent operations.

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

The labeling job details page displays the **All statuses**, **Unlabeled**, and **Labeled** tabs. The **Unlabeled** tab is displayed by default.

#. In the **Unlabeled** tab, click an image. The system automatically directs you to the page for labeling the image. For details about how to use common buttons on this page, see :ref:`Table 2 <en-us_topic_0000002233742232__en-us_topic_0000001139785212_table194471512463>`.

#. Select a labeling method.

   On the labeling page, common :ref:`labeling methods <en-us_topic_0000002233742232__en-us_topic_0000001139785212_table165201739119>` and :ref:`buttons <en-us_topic_0000002233742232__en-us_topic_0000001139785212_table194471512463>` are provided in the toolbar. By default, polygon labeling is selected.

   .. note::

      After you select a method to label the first image, the labeling method automatically applies to subsequent images.


   .. figure:: /_static/images/en-us_image_0000002268741713.png
      :alt: **Figure 1** Toolbar

      **Figure 1** Toolbar

   .. _en-us_topic_0000002233742232__en-us_topic_0000001139785212_table165201739119:

   .. table:: **Table 1** Labeling methods

      +----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Icon     | Description                                                                                                                                                                                                                                                                                           |
      +==========+=======================================================================================================================================================================================================================================================================================================+
      | |image3| | Polygon. In the area where the object to be labeled is located, click to label a point, move the mouse and click multiple points along the edge of the object, and then click the first point again. All the points form a polygon. In this way, the object to be labeled is within the bounding box. |
      +----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0000002233742232__en-us_topic_0000001139785212_table194471512463:

   .. table:: **Table 2** Toolbar buttons

      +-----------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Button    | Features                                                                                                                                               |
      +===========+========================================================================================================================================================+
      | |image13| | Cancel the previous operation.                                                                                                                         |
      +-----------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
      | |image14| | Redo the previous operation.                                                                                                                           |
      +-----------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
      | |image15| | Zoom in an image.                                                                                                                                      |
      +-----------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
      | |image16| | Zoom out an image.                                                                                                                                     |
      +-----------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
      | |image17| | Delete all bounding boxes on the current image.                                                                                                        |
      +-----------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
      | |image18| | Show or hide a bounding box. This operation can be performed only on a labeled image.                                                                  |
      +-----------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
      | |image19| | Drag a bounding box to another position or drag the edge of the bounding box to resize it.                                                             |
      +-----------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
      | |image20| | Reset a bounding box. After dragging a bounding box, you can click this button to quickly restore the bounding box to its original shape and position. |
      +-----------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
      | |image21| | Display the labeled image in full screen.                                                                                                              |
      +-----------+--------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Label an object.

   After labeling an image, click an image that has not been labeled in the image list below to label the new image.

#. Click **Back to Data Labeling Preview** in the upper left part of the page to view the labeling information. In the displayed dialog box, click **Yes** to save the labeling settings.

   The selected images are automatically moved to the **Labeled** tab. In the **Unlabeled** and **All statuses** tabs, the labeling information is updated along with the labeling process, including the added label names and the number of images for each label.

Viewing Labeled Images
----------------------

On the labeling job details page, click the **Labeled** tab to view the list of labeled images. Click an image to view its labeling information in the **File Labels** area on the right.

Modifying a Label
-----------------

After labeling data, you can modify labeled data in the **Labeled** tab.

On the labeling details page, click the **Labeled** tab and then the image to be modified. On the displayed labeling page, modify the labeling information in the **File Labels** area on the right.

-  Modifying a label: In the **Labeling** area, click the edit icon, set the target label name or color in the displayed dialog box, and click |image22| to save the modification. Alternatively, click a label to be modified. In the image labeling area, adjust the position and size of the bounding box. After the adjustment is complete, click another label to save the modification.
-  Modifying image labeling information: In the area for displaying images, click the target bounding box. Then, blue points on the bounding box are displayed. Drag a blue point and adjust the bounding box to the edge of the object.
-  Deleting a label: In the **Labeling** area, click the deletion icon to delete a label from the image. After all labels of an image are deleted, the image is displayed in the **Unlabeled** tab.

After the labeling information is modified, click **Back to Data Labeling Preview** in the upper left part of the page to exit the labeling page. In the displayed dialog box, click **Yes** to save the modification.

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

In the **All statuses**, **Unlabeled**, or **Labeled** tab, select the images to be deleted or click **Select Images on Current Page**, and click **Delete** in the upper left corner to delete them. In the displayed dialog box, select or deselect **Delete the source files from OBS** as required. After confirmation, click **Yes** to delete the images.

If a tick is displayed in the upper left corner of an image, the image is selected. If no image is selected on the page, the **Delete** button is unavailable.

.. note::

   If you select **Delete the source files from OBS**, images stored in the OBS directory will be deleted accordingly. This operation may affect other dataset versions or datasets using those files, for example, leading to an error in page display, training, or inference. Deleted data cannot be recovered. Exercise caution when performing this operation.

.. |image1| image:: /_static/images/en-us_image_0000002233742380.png
.. |image2| image:: /_static/images/en-us_image_0000002233902260.png
.. |image3| image:: /_static/images/en-us_image_0000002233902260.png
.. |image4| image:: /_static/images/en-us_image_0000002233742404.png
.. |image5| image:: /_static/images/en-us_image_0000002233902268.png
.. |image6| image:: /_static/images/en-us_image_0000002233742396.png
.. |image7| image:: /_static/images/en-us_image_0000002268821533.png
.. |image8| image:: /_static/images/en-us_image_0000002233742412.png
.. |image9| image:: /_static/images/en-us_image_0000002268821625.png
.. |image10| image:: /_static/images/en-us_image_0000002233742432.png
.. |image11| image:: /_static/images/en-us_image_0000002233902276.png
.. |image12| image:: /_static/images/en-us_image_0000002268741657.png
.. |image13| image:: /_static/images/en-us_image_0000002233742404.png
.. |image14| image:: /_static/images/en-us_image_0000002233902268.png
.. |image15| image:: /_static/images/en-us_image_0000002233742396.png
.. |image16| image:: /_static/images/en-us_image_0000002268821533.png
.. |image17| image:: /_static/images/en-us_image_0000002233742412.png
.. |image18| image:: /_static/images/en-us_image_0000002268821625.png
.. |image19| image:: /_static/images/en-us_image_0000002233742432.png
.. |image20| image:: /_static/images/en-us_image_0000002233902276.png
.. |image21| image:: /_static/images/en-us_image_0000002268741657.png
.. |image22| image:: /_static/images/en-us_image_0000002233902272.png
