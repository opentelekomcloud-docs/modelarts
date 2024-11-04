:original_name: datalabel-modelarts_0017.html

.. _datalabel-modelarts_0017:

Video Labeling
==============

Model training requires a large amount of labeled video data. Therefore, before the model training, label the unlabeled video files. ModelArts enables you to label video files. In addition, you can modify the labels of video files, or remove their labels and label the video files again.

.. note::

   Video labeling applies only to video frames.

Starting Labeling
-----------------

#. Log in to the ModelArts management console. In the navigation pane on the left, choose **Data Management** > **Label Data**.
#. In the labeling job list, select a labeling type from the **All type** drop-down list, click the job to be performed based on the labeling type. The details page of the job is displayed.
#. The job details page displays all data of the labeling job.

Synchronizing Data Sources
--------------------------

ModelArts automatically synchronizes data and labeling information from **Input Dataset Path** to the dataset details page.

To quickly obtain the latest data in the OBS bucket, in the **Labeled** or **Unlabeled** tab of the labeling job details page, click **Synchronize Data Source**.


Video Labeling
--------------

The labeling job details page displays the **Unlabeled**, **Labeled**, and **All statuses** tabs.

#. In the **Unlabeled** tab, click the target video file in the video list on the left. The labeling page is displayed.

#. Play the video. When the video is played to the time point to be labeled, click the pause button in the progress bar to pause the video to a specific image.

#. .. _en-us_topic_0000002043181000__en-us_topic_0000001185265235_li993163014399:

   In the upper pane, select a bounding box. By default, a rectangular box is selected. Drag the mouse to select an object in the video image, enter a new label name in the displayed **Add Label** text box, select a label color, and click **Add** to label the object. Alternatively, select an existing label from the drop-down list and click **Add** to label the object. Label all objects in the image. Multiple labels can be added to an image.

   The supported labeling boxes are the same as those for object detection. For details, see :ref:`Table 2 <en-us_topic_0000002043180996__en-us_topic_0000001185265231_table194471512463>`.

#. After the previous image is labeled, click the play button on the progress bar to resume the playback. Then, repeat :ref:`3 <en-us_topic_0000002043181000__en-us_topic_0000001185265235_li993163014399>` to complete labeling on the entire video.

   Click **Label List** in the upper right corner of the page. The time points when the video is labeled are displayed.


   .. figure:: /_static/images/en-us_image_0000002043022744.png
      :alt: **Figure 1** File labels

      **Figure 1** File labels

#. Click **Back to Data Labeling Preview** in the upper left corner of the page. The labeling job details page is displayed, and the labeled video file is displayed in the **Labeled** tab.

Modifying Labeled Data
----------------------

After labeling data, you can modify labeled data in the **Labeled** tab.

-  In the **Labeled** tab, click the target video file. In the upper right corner of the labeling page, click **Label List** to go to the **File Labels** page. You can click the triangle icon on the right of the time point to view details, modify labels, and delete labels.

-  Modifying a label: In the **File Labels** area, click the edit button on the right of a label to modify it.
-  Deleting a label: In the **File Labels** area, click the delete button on the right of a label to delete it. If you click the delete icon on the right of the image time, all labels on the image are deleted.

Adding Video Files
------------------

In addition to the data synchronized, you can directly add data on labeling job details page for labeling.

#. On the labeling job details page, click the **Unlabeled** or **Labeled** tab, click **Add data** in the upper left corner.
#. Configure the data source, import mode, and other parameters, and click **OK**.

Deleting a Video File
---------------------

You can quickly delete the video files you want to discard.

In the **All statuses**, **Unlabeled**, or **Labeled** tab, select the video files to be deleted or click **Select Images on Current Page** to select all video files on the page, and click **Delete** in the upper part to delete the video files. In the displayed dialog box, select or deselect **Delete the source files from OBS** as required. After confirmation, click **OK** to delete the videos.

If a tick is displayed in the upper left corner of a video file, the video file is selected. If no video file is selected on the page, the **Delete** button is unavailable.

.. note::

   If you select **Delete the source files from OBS**, video files stored in the corresponding OBS directory will be deleted when you delete the selected video files. Deleting source files may affect other dataset versions or datasets using those files. As a result, the page display, training, or inference is abnormal. Deleted data cannot be recovered. Exercise caution when performing this operation.
