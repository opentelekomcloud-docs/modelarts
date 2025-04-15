:original_name: datalabel-modelarts_0016.html

.. _datalabel-modelarts_0016:

Speech Paragraph Labeling
=========================

Model training requires a large amount of labeled data. Therefore, before the model training, label the unlabeled audio files. ModelArts enables you to label audio files. In addition, you can modify the labels of audio files, or remove their labels and label the audio files again.

Starting Labeling
-----------------

#. Log in to the ModelArts management console. In the navigation pane on the left, choose **Data Management** > **Label Data**.
#. In the labeling job list, select a labeling type from the **All type** drop-down list, click the job to be performed based on the labeling type. The details page of the job is displayed.
#. The job details page displays all data of the labeling job.

Synchronizing Data Sources
--------------------------

ModelArts automatically synchronizes data and labeling information from datasets to the labeling job.

To quickly obtain the latest data in the OBS bucket, click **Synchronize Data Source** in the **Unlabeled** tab of the labeling job details page to add the data uploaded using OBS to the dataset.

Labeling Audio Files
--------------------

The labeling job details page displays the **Unlabeled** and **Labeled** tabs. The **Unlabeled** tab is displayed by default.

#. In the audio file list in the **Unlabeled** tab, click the target audio file. In the area on the right, the audio file is displayed. Click |image1| below the audio file to play the audio.
#. Select an audio segment based on the content being played, and enter the audio file label and content in the **Speech Content** text box.
#. After entering the content, click **Label** to complete the labeling. The audio file is automatically moved to the **Labeled** tab.

Viewing the Labeled Audio Files
-------------------------------

On the labeling job details page, click the **Labeled** tab to view the list of labeled audio files. Click the audio file to view the labeling information on the right.

Modifying Labeled Data
----------------------

After labeling data, you can modify labeled data in the **Labeled** tab.

-  Modifying a label: On the labeling details page, click the **Labeled** tab, and select the audio file to be modified from the audio file list. In the right area, modify labeling information and click **Label** to complete the modification.
-  Deleting a label: Click **Delete** in the **Operation** column of the target number to delete the label of the audio segment. Alternatively, you can click |image2| above the labeled audio file to delete the label. Then click **Label**.

Adding an Audio File
--------------------

In addition to the data synchronized, you can directly add data on labeling job details page for labeling.

#. On the labeling job details page, click the **Unlabeled** tab, click **Add data** in the upper left corner.
#. Configure input data and click **OK**.

Deleting Audio Files
--------------------

You can quickly delete the audio files you want to discard.

In the **Unlabeled** or **Labeled** tab, select the audio files to be deleted, and then click **Delete File** in the upper left corner. In the displayed dialog box, select or deselect **Delete the source files from OBS** as required. After confirmation, click **OK** to delete the audio files.

.. note::

   If you select **Delete the source files from OBS**, audio files stored in the corresponding OBS directory will be deleted when you delete the selected audio files. Deleting source files may affect other dataset versions or datasets using those files. As a result, the page display, training, or inference is abnormal. Deleted data cannot be recovered. Exercise caution when performing this operation.

Managing Annotators
-------------------

If team labeling is enabled for a labeling job, view its labeling details in the **Annotator Management** tab. Additionally, you can add, modify, or delete annotators.

#. Choose **Data Management** > **Label Data**. In the **My Creations** or **My Participations** tab, view the list of all labeling jobs.
#. Locate the target team labeling job. (The name of a team labeling job is followed by |image3|.)
#. Choose **More** > **Annotator Management** in the **Operation** column. Alternatively, click the job name to go to the job details page, and choose **Team Labeling** > **Annotator Management** in the upper right corner.

-  Adding an annotator

   Click **Add Member**, select a member name, and click **OK**.

   Click **Send Email** in the **Operation** column to send the labeling job to the annotator by email.

-  Modifying annotator information

   Click **Modify** in the **Operation** column to modify the role of the annotator.

-  Deleting an annotator

   Click **Delete** in the **Operation** column to delete the annotator.

.. |image1| image:: /_static/images/en-us_image_0000002233902168.png
.. |image2| image:: /_static/images/en-us_image_0000002268741589.png
.. |image3| image:: /_static/images/en-us_image_0000002233742272.png
