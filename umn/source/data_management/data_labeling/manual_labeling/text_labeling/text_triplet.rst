:original_name: datalabel-modelarts_0012.html

.. _datalabel-modelarts_0012:

Text Triplet
============

Triplet labeling is suitable for scenarios where structured information, such as subjects, predicates, and objects, needs to be labeled in statements. With this function, not only entities in statements, but also relationships between entities can be labeled. Triplet labeling is often used in natural language processing tasks such as dependency syntax analysis and information extraction.

Text triplet labeling involves two classes of important labels: **Entity Label** and **Relationship Label**. For **Relationship Label**, set its **Source entity** and **Target entity**.

-  You can define multiple entity and relationship labels for a text object.
-  The **Entity Label** defined during dataset creation cannot be deleted.

Precautions
-----------

Before labeling, ensure that the **Entity Label** and **Relationship Label** of a labeling job have been defined. For **Relationship Label**, set its **Source entity** and **Target entity**. **Relationship Label** must be between the defined **Source entity** and **Target entity**.

For example, if two entities are labeled as **Place**, you cannot add any relationship label between them. If a relationship label cannot be added, a red cross is displayed.

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

#. In the **Unlabeled** tab, the objects to be labeled are listed in the left pane. In the list, click a text object, select the corresponding text content on the right pane, and select an entity name from the displayed entity list to label the content.
#. After labeling multiple entities, click the source entity and target entity in sequence and select a relationship type from the displayed relationship list to label the relationship.
#. After all objects are labeled, click **Save Current Page** at the bottom of the page.

.. note::

   You cannot modify the labels of a dataset in the text triplet type on the labeling page. Instead, click **Label Management** and modify the **Entity Label** and **Relationship Label**.

Modifying Labeled Data
----------------------

After labeling data, you can modify labeled data in the **Labeled** tab.

On the labeling job details page, click the **Labeled** tab. Select a text object in the left pane and the right pane displays the detailed label information. You can move your cursor to the entity or relationship label, and right-click to delete it. You can also click the source entity and target entity in sequence to add a relationship label.

Adding a File
-------------

In addition to the data synchronized, you can directly add data on labeling job details page for labeling.

#. On the labeling job details page, click the **Unlabeled** tab, click **Add data** in the upper left corner.

#. Configure input data and click **OK**.

   For details about how to import data, see section "Importing Data".

Deleting a File
---------------

You can quickly delete the files you want to discard.

-  In the **Unlabeled** tab, select the text to be deleted, and click **Delete** in the upper left corner.
-  In the **Labeled** tab, select the text to be deleted, and click **Delete**. Alternatively, tick **Select Current Page** to select all text objects on the current page and click **Delete** in the upper left corner.

The background of the selected text is blue. If no text is selected on the page, the **Delete** button is unavailable.

Managing Annotators
-------------------

If team labeling is enabled for a labeling job, view its labeling details in the **Annotator Management** tab. Additionally, you can add, modify, or delete annotators.

#. Choose **Data Management** > **Label Data**. In the **My Creations** or **My Participations** tab, view the list of all labeling jobs.
#. Locate the target team labeling job. (The name of a team labeling job is followed by |image1|.)
#. Choose **More** > **Annotator Management** in the **Operation** column. Alternatively, click the job name to go to the job details page, and choose **Team Labeling** > **Annotator Management** in the upper right corner.

-  Adding an annotator

   Click **Add Member**, select a member name, and click **OK**.

   Click **Send Email** in the **Operation** column to send the labeling job to the annotator by email.

-  Modifying annotator information

   Click **Modify** in the **Operation** column to modify the role of the annotator.

-  Deleting an annotator

   Click **Delete** in the **Operation** column to delete the annotator.

.. |image1| image:: /_static/images/en-us_image_0000002374731909.png
