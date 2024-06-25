:original_name: datalabel-modelarts_0014.html

.. _datalabel-modelarts_0014:

Sound classification
====================

Model training requires a large amount of labeled data. Therefore, before the model training, label the unlabeled audio files. ModelArts enables you to label audio files in batches by one click. In addition, you can modify the labels of audio files, or remove their labels and label the audio files again.

Starting Labeling
-----------------

#. Log in to the ModelArts management console. In the navigation pane on the left, choose **Data Management** > **Label Data**.
#. In the labeling job list, select a labeling type from the **All type** drop-down list, click the job to be performed based on the labeling type. The details page of the job is displayed.
#. The job details page displays all data of the labeling job.

Synchronizing New Data
----------------------

ModelArts automatically synchronizes data and labeling information from datasets to the labeling job.

To quickly obtain the latest data in the datasets, in the **Unlabeled** or **Labeled** tab of the labeling job details page, click **Synchronize New Data**.

Labeling Audio Files
--------------------

The labeling job details page displays the **Unlabeled** and **Labeled** tabs. The **Unlabeled** tab is displayed by default. Click |image1| on the left of the audio to preview the audio.

#. In the **Unlabeled** tab, select the audio files to be labeled.

   -  Manual selection: In the audio list, click the target audio. If the blue check box is displayed in the upper right corner, the audio is selected. You can select multiple audio files of the same type and label them together.
   -  Batch selection: If all audio files of the current page belong to one type, you can click **Select Current Page** in the upper right corner of the list to select all the audio files on the page.

#. Add labels.

   a. In the label adding area on the right, set a label in the **Label** text box.

      Method 1 (the required label already exists): In the right pane, select a shortcut from the **Shortcut** drop-down list, select an existing label name from the **Label** text box, and click **OK**.

      Method 2 (adding a label): In the right pane, select a shortcut from the **Shortcut** drop-down list, and enter a new label name in the **Label** text box.

   b. The selected audio files are automatically moved to the **Labeled** tab. In the **Unlabeled** tab, the labeling information is updated along with the labeling process, including the added label names and the number of audio files corresponding to each label.

   .. note::

      **Shortcut key description**: After specifying a shortcut key for a label, you can select an audio file and press the shortcut key to add a label for the audio file. Example: Specify **1** as the shortcut key for the **aa** label. Select one or more files and press **1**. A message is displayed, asking you whether to label the files with **aa**. Click **OK**.

      Each label has a shortcut key. A shortcut key cannot be specified for different labels. Shortcut keys can greatly improve the labeling efficiency.

Viewing the Labeled Audio Files
-------------------------------

On the labeling job details page, click the **Labeled** tab to view the list of labeled audio files. Click an audio file. You can view the label information about the audio file in the **File Labels** area on the right.

Modifying Labeled Data
----------------------

After labeling data, you can modify labeled data in the **Labeled** tab.

-  **Modifying based on audio**

   On the labeling job details page, click the **Labeled** tab. Select one or more audio files to be modified from the audio list. Modify the label in the label details area on the right.

   -  Modifying a label: In the **File Labels** area, click the edit icon in the **Operation** column, enter the correct label name in the text box, and click the check mark to complete the modification.
   -  Deleting a label: In the **File Labels** area, click the delete icon in the **Operation** column to delete the label.

-  **Modifying based on labels**

   On the labeling job details page, click the **Labeled** tab. The information about all labels is displayed on the right.

   -  Modifying a label: Click the edit icon in the **Operation** column. In the displayed dialog box, enter the new label name and click **OK**. After the modification, the new label applies to the audio files that contain the original label.
   -  Deleting a label: Click the deletion icon in the **Operation** column. In the displayed dialog box, select the object to be deleted as prompted and click **OK**.

Adding an Audio File
--------------------

In addition to the data synchronized, you can directly add data on labeling job details page for labeling.

#. On the labeling job details page, click the **Unlabeled** or **Labeled** tab, click **Add data** in the upper left corner.

#. Configure the data source, import mode, and other parameters, and click **OK**.

   For details about how to import data, see section "Importing Data".

Deleting Audio Files
--------------------

You can quickly delete the audio files you want to discard.

In the **Unlabeled** or **Labeled** tab, select the audio files to be deleted one by one or tick **Select Current Page** to select all audio files on the page, and then click **Delete File** in the upper left corner. In the displayed dialog box, select or deselect **Delete the source files from OBS** as required. After confirmation, click **OK** to delete the audio files.

If a tick is displayed in the upper right corner of an audio file, the audio file is selected. If no audio file is selected on the page, the **Delete File** button is unavailable.

.. note::

   If you select **Delete the source files from OBS**, audio files stored in the corresponding OBS directory will be deleted when you delete the selected audio files. Deleting source files may affect other dataset versions or datasets using those files. As a result, the page display, training, or inference is abnormal. Deleted data cannot be recovered. Exercise caution when performing this operation.

.. |image1| image:: /_static/images/en-us_image_0000001910067714.png
