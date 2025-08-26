:original_name: dataprepare-modelarts-0012.html

.. _dataprepare-modelarts-0012:

Importing Data from an OBS Path
===============================

Prerequisites
-------------

-  You have created a dataset.
-  You have stored the data to be imported in OBS. You have stored the manifest file in OBS.
-  The OBS bucket and ModelArts are in the same region and you can operate the bucket.

Importing File Data from an OBS Path
------------------------------------

The parameters on the GUI for data import vary according to the dataset type. The following uses a dataset of the image classification type as an example.

#. Log in to the ModelArts management console. In the navigation pane on the left, choose **Data Management** > **Datasets**.

#. Locate the target dataset and click **Import** in the **Operation** column. Alternatively, you can click the dataset name to go to the **Dashboard** tab of the dataset, and click **Import** in the upper right corner.

#. In the **Import** dialog box, set the parameters as follows and click **OK**.

   -  **Data Source**: **OBS**

   -  **Import Mode**: **Path**

   -  **Import Path**: OBS path for storing data

   -  **Labeling Status**: **Labeled**

   -  **Advanced Feature Settings**: This function is disabled by default. You can click the button on the right to enable this function.

      **Import by Tag** enables the system to automatically obtain the labels of the current dataset. Click **Add Label** to add a label. This field is optional. After importing the data, you can add or delete labels during data labeling.

   After the data is imported, it will be automatically synchronized to the dataset. On the **Datasets** page, click the dataset name to view its details and create a labeling job to label the data.

Labeling Status of File Data
----------------------------

The labeling status can be **Unlabeled** or **Labeled**.

-  **Unlabeled**: Only the labeling object (such as unlabeled images or texts) is imported.

-  **Labeled**: Both the labeling object and content are imported. Labeling content importing is not supported for datasets in free format.

   To ensure that the labeling content can be correctly read, you must store data in strict accordance with the specifications.

   If **Import Mode** is set to **Path**, store the data to be imported according to the labeling file specifications. For details, see :ref:`Specifications for Importing Data from an OBS Directory <dataprepare-modelarts-0013>`.

   If **Import Mode** is set to **manifest**, the manifest file specifications must be met.

   .. note::

      -  If the labeling status is set to **Labeled**, ensure that the folder or manifest file complies with the format specifications. Otherwise, the import may fail.
      -  After the labeled file is imported, check whether the imported data is in the labeled state.

Importing a Table Dataset from OBS
----------------------------------

ModelArts allows you to import table data (CSV files) from OBS.

Import description:

-  The prerequisite for successful import is that the schema of the data source must be the same as that specified during dataset creation. The schema indicates column names and types of a table. Once specified during dataset creation, the values cannot be changed.
-  When a CSV file is imported from OBS, the data type is not validated, but the number of columns must be the same as that in the schema of the dataset. If the data format is invalid, the data is set to null. For details, see :ref:`Table 3 <en-us_topic_0000002340893974__table5251155510463>`.
-  You must select the directory where the CSV file is stored. The number of columns in the CSV file must be the same as that in the dataset schema. The schema of the CSV file can be automatically obtained.

.. code-block::

   ├─dataset-import-example
   │      table_import_1.csv
   │      table_import_2.csv
   │      table_import_3.csv
   │      table_import_4.csv
