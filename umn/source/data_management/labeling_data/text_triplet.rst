.. _modelarts_23_0211:

Text Triplet
============

Triplet labeling is suitable for scenarios where structured information, such as subjects, predicates, and objects, needs to be labeled in statements. With this function, not only entities in statements, but also relationships between entities can be labeled. Triplet labeling is often used in natural language processing tasks such as dependency syntax analysis and information extraction.

Text triplet labeling involves two classes of important labels: **Entity Label** and **Relationship Label**. For the **Relationship Label**, you need to set its **Source entity** and **Target entity**.

-  You can define multiple entity and relationship labels for a text object.
-  The **Entity Label** defined during dataset creation cannot be deleted.

Precautions
-----------

Before labeling, ensure that the **Entity Label** and **Relationship Label** of a dataset have been defined. For the **Relationship Label**, you need to set its **Source entity** and **Target entity**. The **Relationship Label** must be between the defined **Source entity** and **Target entity**.

For example, if two entities are labeled as **Place**, you cannot add any relationship label between them. If a relationship label cannot be added, a red cross is displayed.

Starting Labeling
-----------------

#. Log in to the ModelArts management console. In the left navigation pane, choose **Data Management** > **Datasets**. The **Datasets** page is displayed.

#. In the dataset list, select the dataset to be labeled based on the labeling type, and click the dataset name to go to the **Dashboard** tab page of the dataset.

   By default, the **Dashboard** tab page of the current dataset version is displayed. If you need to label the dataset of another version, click the **Versions** tab and then click **Set to Current Version** in the right pane. For details, see :ref:`Managing Dataset Versions <modelarts_23_0019>`.

#. On the **Dashboard** page of the dataset, click **Label** in the upper right corner. The dataset details page is displayed. By default, all data of the dataset is displayed on the dataset details page.

.. _modelarts_23_0211__en-us_topic_0209128667_section888019266174:

Labeling Content
----------------

The dataset details page displays the labeled and unlabeled text objects in the dataset. The **Unlabeled** tab page is displayed by default.

#. On the **Unlabeled** tab page, the objects to be labeled are listed in the left pane. In the list, click a text object, select the corresponding text content on the right pane, and select an entity name from the displayed entity list to label the content.

   .. _modelarts_23_0211__en-us_topic_0209128667_fig127381972311:

   .. figure:: /_static/images/en-us_image_0000001110760968.png
      :alt: **Figure 1** Labeling an entity
   

      **Figure 1** Labeling an entity

#. After labeling multiple entities, click the source entity and target entity in sequence and select a relationship type from the displayed relationship list to label the relationship.

   .. _modelarts_23_0211__en-us_topic_0209128667_fig16874184518477:

   .. figure:: /_static/images/en-us_image_0000001110920874.png
      :alt: **Figure 2** Labeling a relationship
   

      **Figure 2** Labeling a relationship

#. After all objects are labeled, click **Save Current Page** at the bottom of the page.

.. note::

   You cannot modify the labels of a dataset in the text triplet type on the labeling page. Instead, click **Edit** to enter the **Modify Dataset** page and modify the **Entity Label** and **Relationship Label**.

Modifying Labeled Data
----------------------

After labeling data, you can modify labeled data on the **Labeled** tab page.

On the dataset details page, click the **Labeled** tab. Select a text object in the left pane and the right pane displays the detailed label information. You can move your cursor to the entity or relationship label, and right-click to delete it. You can also click the source entity and target entity in sequence to add a relationship label.

You can click **Delete Labels on Current Item** at the bottom of the page to delete all labels in the selected text object.

Adding a File
-------------

In addition to automatically synchronizing data from **Input Dataset Path**, you can directly add text files on ModelArts for data labeling.

#. On the dataset details page, click the **Unlabeled** tab. Then click **Add File**.

#. In the **Add File** dialog box that is displayed, select the files to be uploaded.

   Select one or more files to be uploaded in the local environment. Only **.txt** and **.csv** files are supported. The total size of files uploaded at a time cannot exceed 8 MB.

#. In the **Add File** dialog box, click **Upload**. The files you add will be automatically displayed in the **Labeling Objects** list on the **Unlabeled** tab page.

Deleting a File
---------------

You can quickly delete the files you want to discard.

-  On the **Unlabeled** tab page, select the text to be deleted, and click **Delete** in the upper left corner to delete the text.
-  On the **Labeled** tab page, select the text to be deleted and click **Delete**. Alternatively, you can tick **Select Images on Current Page** to select all text objects on the current page and click **Delete** in the upper left corner.

The background of the selected text is blue. If no text is selected on the page, the **Delete** button is unavailable.
