:original_name: datalabel-modelarts_0015.html

.. _datalabel-modelarts_0015:

Speech Labeling
===============

Model training requires a large amount of labeled data. Therefore, before the model training, label the unlabeled audio files. ModelArts enables you to label audio files in batches by one click. In addition, you can modify the labels of audio files, or remove their labels and label the audio files again.

Starting Labeling
-----------------

#. Log in to the ModelArts management console. In the navigation pane on the left, choose **Data Management** > **Label Data**.
#. In the labeling job list, select a labeling type from the **All type** drop-down list, click the job to be performed based on the labeling type. The details page of the job is displayed.
#. The job details page displays all data of the labeling job.

Synchronizing New Data
----------------------

ModelArts automatically synchronizes data and labeling information from datasets to the labeling job.

To quickly obtain the latest data in the datasets, in the **Unlabeled** tab of the labeling job details page, click **Synchronize New Data**.

Labeling Audio Files
--------------------

The labeling job details page displays the labeled and unlabeled audio files. The **Unlabeled** tab is displayed by default.

#. In the audio file list in the **Unlabeled** tab, click the target audio file. In the area on the right, the audio file is displayed. Click |image1| below the audio file to play the audio.
#. In **Speech Content**, enter the speech content.
#. After entering the content, click **Label** to complete the labeling. The audio file is automatically moved to the **Labeled** tab.

Viewing the Labeled Audio Files
-------------------------------

On the labeling job details page, click the **Labeled** tab to view the list of labeled audio files. Click the audio file to view the audio content in the **Speech Content** text box on the right.

Modifying Labeled Data
----------------------

After labeling data, you can modify labeled data in the **Labeled** tab.

On the labeling job details page, click the **Labeled** tab and select the audio file to be modified from the audio file list. In the label information area on the right, modify the content of the **Speech Content** text box, and click **Label** to complete the modification.

Adding an Audio File
--------------------

In addition to the data synchronized, you can directly add data on labeling job details page for labeling.

#. On the labeling job details page, click the **Unlabeled** tab, click **Add data** in the upper left corner.

#. Configure input data and click **OK**.

   For details about how to import data, see section "Importing Data".

Deleting Audio Files
--------------------

You can quickly delete the audio files you want to discard.

In the **Unlabeled** or **Labeled** tab, select the audio files to be deleted, and then click **Delete File** in the upper left corner. In the displayed dialog box, select or deselect **Delete the source files from OBS** as required. After confirmation, click **OK** to delete the audio files.

.. note::

   If you select **Delete the source files from OBS**, audio files stored in the corresponding OBS directory will be deleted when you delete the selected audio files. Deleting source files may affect other dataset versions or datasets using those files. As a result, the page display, training, or inference is abnormal. Deleted data cannot be recovered. Exercise caution when performing this operation.

.. |image1| image:: /_static/images/en-us_image_0000002233902100.png
