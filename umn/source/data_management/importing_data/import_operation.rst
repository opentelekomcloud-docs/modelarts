.. _modelarts_23_0006:

Import Operation
================

After a dataset is created, you can directly synchronize data from the dataset. Alternatively, you can import more data by importing the dataset. Data can be imported from an OBS directory or the manifest file.

Prerequisites
-------------

-  You have created a dataset.
-  You have stored the data to be imported in OBS. You have stored the manifest file in OBS.
-  The OBS buckets and ModelArts are in the same region.

Import Modes
------------

There are two import modes: **OBS path** and **Manifest file**.

-  **OBS path**: indicates that the dataset to be imported has been stored in an OBS directory in advance. In this case, you need to select an OBS path that you can access. In addition, the directory structure in the OBS path must comply with the specifications. For details, see :ref:`Specifications for Importing Data from an OBS Directory <modelarts_23_0008>`. Only the following types of dataset support the **OBS path** import mode: **Image classification**, **Object detection**, **Text classification**, **Table**, and **Sound classification**.
-  **Manifest file**: indicates that the dataset file is in the manifest format and data is imported from the manifest file. The manifest file defines the mapping between labeling objects and content. In addition, the manifest file has been uploaded to OBS. For details about the specifications of the manifest file, see :ref:`Specifications for Importing the Manifest File <modelarts_23_0009>`.

.. note::

   Before importing an object detection dataset, ensure that the labeling range of the labeling file does not exceed the size of the original image. Otherwise, the import may fail.

.. table:: **Table 1** Import modes supported by datasets

   +---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Dataset Type              | Importing Data from an OBS Path                                                                                                              | Importing Data from a Manifest File                                                                                                              |
   +===========================+==============================================================================================================================================+==================================================================================================================================================+
   | Image classification      | Supported                                                                                                                                    | Supported                                                                                                                                        |
   |                           |                                                                                                                                              |                                                                                                                                                  |
   |                           | Follow the format specifications described in :ref:`Image Classification <modelarts_23_0008__en-us_topic_0170886816_section570816190577>`.   | Follow the format specifications described in :ref:`Image Classification <modelarts_23_0009__en-us_topic_0170886817_section260132417144>`.       |
   +---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Object detection          | Supported                                                                                                                                    | Supported                                                                                                                                        |
   |                           |                                                                                                                                              |                                                                                                                                                  |
   |                           | Follow the format specifications described in :ref:`Object Detection <modelarts_23_0008__en-us_topic_0170886816_section1371122614572>`.      | Follow the format specifications described in :ref:`Object Detection <modelarts_23_0009__en-us_topic_0170886817_section1571582442114>`.          |
   +---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Image segmentation        | Supported                                                                                                                                    | Supported                                                                                                                                        |
   |                           |                                                                                                                                              |                                                                                                                                                  |
   |                           | Follow the format specifications described in :ref:`Image Segmentation <modelarts_23_0008__en-us_topic_0170886816_section1363851815518>`.    | Follow the format specifications described in :ref:`Image Segmentation <modelarts_23_0009__en-us_topic_0170886817_section6459163044216>`.        |
   +---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Sound classification      | Supported                                                                                                                                    | Supported                                                                                                                                        |
   |                           |                                                                                                                                              |                                                                                                                                                  |
   |                           | Follow the format specifications described in :ref:`Sound Classification <modelarts_23_0008__en-us_topic_0170886816_section1683314458578>`.  | Follow the format specifications described in :ref:`Sound Classification <modelarts_23_0009__en-us_topic_0170886817_section2373122922115>`.      |
   +---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Speech labeling           | N/A                                                                                                                                          | Supported                                                                                                                                        |
   |                           |                                                                                                                                              |                                                                                                                                                  |
   |                           |                                                                                                                                              | Follow the format specifications described in :ref:`Speech Paragraph Labeling <modelarts_23_0009__en-us_topic_0170886817_section1260563812219>`. |
   +---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Speech paragraph labeling | N/A                                                                                                                                          | Supported                                                                                                                                        |
   |                           |                                                                                                                                              |                                                                                                                                                  |
   |                           |                                                                                                                                              | Follow the format specifications described in :ref:`Speech Labeling <modelarts_23_0009__en-us_topic_0170886817_section10586153472113>`.          |
   +---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Text classification       | Supported                                                                                                                                    | Supported                                                                                                                                        |
   |                           |                                                                                                                                              |                                                                                                                                                  |
   |                           | Follow the format specifications described in :ref:`Text Classification <modelarts_23_0008__en-us_topic_0170886816_section163641141195713>`. | Follow the format specifications described in :ref:`Text Classification <modelarts_23_0009__en-us_topic_0170886817_section8593163192118>`.       |
   +---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Named entity recognition  | N/A                                                                                                                                          | Supported                                                                                                                                        |
   |                           |                                                                                                                                              |                                                                                                                                                  |
   |                           |                                                                                                                                              | Follow the format specifications described in :ref:`Named Entity Recognition <modelarts_23_0009__en-us_topic_0170886817_section335761812211>`.   |
   +---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Text triplet              | N/A                                                                                                                                          | Supported                                                                                                                                        |
   |                           |                                                                                                                                              |                                                                                                                                                  |
   |                           |                                                                                                                                              | Follow the format specifications described in :ref:`Text Triplet <modelarts_23_0009__en-us_topic_0170886817_section29512198>`.                   |
   +---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Table                     | Supported                                                                                                                                    | N/A                                                                                                                                              |
   |                           |                                                                                                                                              |                                                                                                                                                  |
   |                           | Follow the format specifications described in :ref:`Table <modelarts_23_0008__en-us_topic_0170886816_section1171862514918>`.                 |                                                                                                                                                  |
   +---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Video                     | N/A                                                                                                                                          | Supported                                                                                                                                        |
   |                           |                                                                                                                                              |                                                                                                                                                  |
   |                           |                                                                                                                                              | Follow the format specifications described in :ref:`Video Labeling <modelarts_23_0009__en-us_topic_0170886817_section1269454020180>`.            |
   +---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Free format               | N/A                                                                                                                                          | N/A                                                                                                                                              |
   +---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+

Importing Data from an OBS Path
-------------------------------

The parameters on the GUI for data import vary according to the dataset type. The following uses a dataset of the image classification type as an example.

#. Log in to the ModelArts management console. In the left navigation pane, choose **Data Management** > **Datasets**. The **Datasets** page is displayed.

#. Locate the row that contains the desired dataset and choose **More > Import** in the **Operation** column.

   Alternatively, you can click the dataset name to go to the **Dashboard** tab page of the dataset, and click **Import** in the upper right corner.

#. In the **Import** dialog box, set **Import Mode** to **OBS path** and set **OBS path** to the path for storing data. Then click **OK**.

   After the data import is successful, the data is automatically synchronized to the dataset. On the **Datasets** page, you can click the dataset name to view its details and label the data.

Importing Data from a Manifest File
-----------------------------------

The parameters on the GUI for data import vary according to the dataset type. The following uses a dataset of the object detection type as an example. Datasets of the table type cannot be imported from the manifest file.

#. Log in to the ModelArts management console. In the left navigation pane, choose **Data Management** > **Datasets**. The **Datasets** page is displayed.

#. Locate the row that contains the desired dataset and choose **More > Import** in the **Operation** column.

   Alternatively, you can click the dataset name to go to the **Dashboard** tab page of the dataset, and click **Import** in the upper right corner.

#. In the **Import** dialog box, set the parameters as follows and click **OK**.

   -  **Import Mode**: Select **Manifest file**.
   -  **Manifest file**: Select the OBS path for storing the manifest file.
   -  **Import by Label**: The system automatically obtains the labels of the dataset. You can click **Add Label** to add a label or click the deletion icon on the right to delete a label. This field is optional. After importing a dataset, you can add or delete labels during data labeling.
   -  **Import labels**: If this parameter is selected, the labels defined in the manifest file are imported to the ModelArts dataset.

   After the data import is successful, the data is automatically synchronized to the dataset. On the **Datasets** page, you can click the dataset name to go to the **Dashboard** tab page of the dataset, and click **Label** in the upper right corner. On the displayed dataset details page, view detailed data and label data.
