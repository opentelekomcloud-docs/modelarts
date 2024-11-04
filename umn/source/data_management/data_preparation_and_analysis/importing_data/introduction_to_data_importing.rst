:original_name: dataprepare-modelarts-0008.html

.. _dataprepare-modelarts-0008:

Introduction to Data Importing
==============================

After a dataset is created, you can import more data. ModelArts allows you to import data from different data sources.

-  :ref:`Importing Data from OBS <dataprepare-modelarts-0010>`
-  :ref:`Importing Data from Local Files <dataprepare-modelarts-0019>`

ModelArts AI Gallery provides a large number of built-in datasets, including file and table datasets. You can download and use the built-in datasets from AI Gallery. You can also import your data to ModelArts.

File Data Sources
-----------------

You can import data by downloading built-in datasets from AI Gallery, or from OBS or a local file. After the import, the data from the import path is automatically synchronized to the data source path of the dataset.

-  **OBS**: Import data from an OBS path or a manifest file.
-  **Local file**: Import local data that has been uploaded to an OBS path.

Table Data Sources
------------------

You can import data by downloading built-in datasets from AI Gallery, or from OBS, GaussDB(DWS), DLI, MRS, and local files.

.. _en-us_topic_0000002043025308__section2764112633219:

Import Mode
-----------

There are five modes for importing data to a dataset.

-  When you create a dataset, select an import path. The data is automatically synchronized from the import path.
-  After a dataset is created, click **Import** in the **Operation** column on the dataset list page.
-  On the dataset list page, click a dataset. On the dataset details page, choose **Import** > **Import**.
-  On the dataset list page, click a dataset. On the dataset details page, click **Synchronize Data Source** to synchronize data from OBS.
-  Add data on the labeling job details page.
