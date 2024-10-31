:original_name: datalabel-modelarts_0011.html

.. _datalabel-modelarts_0011:

Named Entity Recognition
========================

Named entity recognition assigns labels to named entities in text, such as time and locations. Before labeling, pay attention to the following:

A label name of a named entity can contain a maximum of 1,024 characters, including letters, digits, hyphens (-), underscores (_), and special characters.

Starting Labeling
-----------------

#. Log in to the ModelArts management console. In the navigation pane on the left, choose **Data Management** > **Label Data**.
#. In the labeling job list, select a labeling type from the **All type** drop-down list, click the job to be performed based on the labeling type. The details page of the job is displayed.
#. The job details page displays all data of the labeling job.

Synchronizing New Data
----------------------

ModelArts automatically synchronizes data and labeling information from datasets to the labeling job.

To quickly obtain the latest data in the datasets, in the **Unlabeled** tab of the labeling job details page, click **Synchronize New Data**.

Labeling Text Files
-------------------

The labeling job details page displays the **Unlabeled** and **Labeled** tabs. The **Unlabeled** tab is displayed by default.

#. In the **Unlabeled** tab, the objects to be labeled are listed in the left pane. In the list, click the text object to be labeled, select a part of text displayed under **Label Set** for labeling, and select a label in the **Label Set** area in the right pane. Multiple labels can be added to a labeling object.

   You can repeat this operation to select objects and add labels to the objects.

#. Click **Save Current Page** in the lower part of the page to complete the labeling.

Adding a Label
--------------

-  Adding labels in the **Unlabeled** tab: Click the plus sign (+) next to **Label Set**. On the displayed **Add Label** page, add a label name, select a label color, and click **OK**.
-  Adding labels in the **Labeled** tab: Click the plus sign (+) next to **Label Set**. On the displayed **Add Label** page, add a label name, select a label color, and click **OK**.

Viewing the Labeled Text
------------------------

On the dataset details page, click the **Labeled** tab to view the list of the labeled text. You can also view all labels supported by the dataset in the **All Labels** area on the right.

Modifying Labeled Data
----------------------

After labeling data, you can modify labeled data in the **Labeled** tab.

On the labeling job details page, click the **Labeled** tab, and modify the text information in the label information area on the right.

-  **Modifying based on texts**

   On the labeling job details page, click the **Labeled** tab, and select the text to be modified from the text list.

   Manual deletion: In the text list, click the text. When the text background turns blue, the text is selected. On the right of the page, click |image1| on the above to delete the label.

-  **Modifying based on labels**

   On the labeling job details page, click the **Labeled** tab. The information about all labels is displayed on the right.

   -  Batch modification: In the **All Labels** area, click the edit icon in the **Operation** column, add a label name in the text box, select a label color, and click **OK**.
   -  Batch deletion: In the **All Labels** area, click the deletion icon in the **Operation** column to delete the label. In the displayed dialog box, select **Delete the label** or **Delete the label and objects with only the label**, and click **OK**.

Adding a File
-------------

In addition to the data synchronized, you can directly add data on labeling job details page for labeling.

#. On the labeling job details page, click the **Unlabeled** tab, click **Add data** in the upper left corner.

#. Configure the data source, import mode, and other parameters, and click **OK**.

   For details about how to import data, see section "Importing Data".

Deleting a File
---------------

You can quickly delete the files you want to discard.

-  In the **Unlabeled** tab, select the text to be deleted, and click **Delete** in the upper left corner.
-  In the **Labeled** tab, select the text to be deleted, and click **Delete**. Alternatively, tick **Select Current Page** to select all text objects on the current page and click **Delete** in the upper left corner.

The background of the selected text is blue.

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

.. |image1| image:: /_static/images/en-us_image_0000002079180357.png
.. |image2| image:: /_static/images/en-us_image_0000002079101757.png
