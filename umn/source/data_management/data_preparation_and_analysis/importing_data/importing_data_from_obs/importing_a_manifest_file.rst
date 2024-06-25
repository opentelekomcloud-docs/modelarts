:original_name: dataprepare-modelarts-0014.html

.. _dataprepare-modelarts-0014:

Importing a Manifest File
=========================

Prerequisites
-------------

-  You have created a dataset.
-  You have stored the data to be imported in OBS. You have stored the manifest file in OBS.
-  The OBS bucket and ModelArts are in the same region and you can operate the bucket.

Importing File Data from a Manifest File
----------------------------------------

The parameters on the GUI for data import vary according to the dataset type. The following uses an image dataset as an example.

#. Log in to the ModelArts management console. In the navigation pane on the left, choose **Data Management** > **Datasets**.

#. Locate the row that contains the desired dataset and click **Import** in the **Operation** column. Alternatively, you can click the dataset name to go to the **Dashboard** tab of the dataset, and click **Import** in the upper right corner.

#. In the **Import** dialog box, set the parameters as follows and click **OK**.

   -  **Data Source**: **OBS**

   -  **Import Mode**: **manifest**

   -  **Manifest File**: OBS path for storing the manifest file

   -  **Labeling Status**: **Labeled**

   -  **Advanced Feature Settings**: disabled by default

      **Import by Tag** The system automatically obtains the labels of the dataset. You can click **Add Label** to add a label. This parameter is optional. If **Import by Tag** is disabled, you can add or delete labels for imported data when labeling data.

      **Import Only Hard Examples**: If this parameter is selected, only the **hard** attribute data of the manifest file is imported.

   After the data is imported, it will be automatically synchronized to the dataset. On the **Datasets** page, click the dataset name to view its details and create a labeling job to label the data.

Labeling Status of File Data
----------------------------

The labeling status can be **Unlabeled** or **Labeled**.

-  **Unlabeled**: Only the labeling object (such as unlabeled images or texts) is imported.

-  **Labeled**: Both the labeling object and content are imported. Labeling content importing is not supported for datasets in free format.

   To ensure that the labeling content can be correctly read, you must store data in strict accordance with the specifications.

   If **Import Mode** is set to **Path**, store the data to be imported according to the labeling file specifications.

   If **Import Mode** is set to **manifest**, the manifest file specifications must be met. For details, see :ref:`Specifications for Importing a Manifest File <dataprepare-modelarts-0015>`.

   .. note::

      If the labeling status is set to **Labeled**, ensure that the folder or manifest file complies with the format specifications. Otherwise, the import may fail.
