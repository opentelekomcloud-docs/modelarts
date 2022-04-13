.. _modelarts_23_0003:

Introduction to Data Management
===============================

In ModelArts, you can import and label data on the **Data Management** page to prepare for model building. ModelArts uses datasets as the basis for model development or training.

.. _modelarts_23_0003__en-us_topic_0171496996_section51771731153811:

Dataset Types
-------------

ModelArts supports datasets of images, audio, text, tables, videos, and other types for the following purposes:

-  Images

   -  Image classification: identifies a class of objects in images.
   -  Object detection: identifies the position and class of each object in an image.
   -  Image segmentation: identifies the outline of each object in an image.

-  Audio

   -  Sound classification: classifies and identifies different sounds.
   -  Speech labeling: labels speech content.
   -  Speech paragraph labeling: segments and labels speech content.

-  Text

   -  Text classification: assigns labels to text according to its content.
   -  Named entity recognition: assigns labels to named entities in text, such as time and locations.
   -  Text triplet: assigns labels to entity segments and entity relationships in the text.

-  Tables

   -  Table: applies to structured data processing such as tables. The file format can be CSV. You can preview a maximum of 100 records in a table.

-  Videos

   -  Video labeling: identifies the position and class of each object in a video. Only the MP4 format is supported.

-  Others

   -  Free format: manages data in any format. Labeling is not available for data of the free format type. The free format type is applicable to scenarios where labeling is not required or developers customize labeling. If your dataset needs to contain data in multiple formats or your data format does not meet the requirements of other types of datasets, you can select a dataset in free format.

      .. _modelarts_23_0003__en-us_topic_0171496996_fig594265714140:

      .. figure:: /_static/images/en-us_image_0000001156920919.png
         :alt: **Figure 1** Example of a dataset in free format
      

         **Figure 1** Example of a dataset in free format

Dataset Management Process and Functions
----------------------------------------

.. table:: **Table 1** Function description

   +----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Function                                                 | Description                                                                                                                                                                                 |
   +==========================================================+=============================================================================================================================================================================================+
   | :ref:`Creating a Dataset <modelarts_23_0004>`            | Create a dataset.                                                                                                                                                                           |
   +----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Image Classification <modelarts_23_0011>`          | Label data based on the types of datasets. Data labeling is not supported for datasets in free format or table format.                                                                      |
   |                                                          |                                                                                                                                                                                             |
   | :ref:`Object Detection <modelarts_23_0012>`              |                                                                                                                                                                                             |
   |                                                          |                                                                                                                                                                                             |
   | :ref:`Text Classification <modelarts_23_0013>`           |                                                                                                                                                                                             |
   |                                                          |                                                                                                                                                                                             |
   | :ref:`Named Entity Recognition <modelarts_23_0014>`      |                                                                                                                                                                                             |
   |                                                          |                                                                                                                                                                                             |
   | :ref:`Text Triplet <modelarts_23_0211>`                  |                                                                                                                                                                                             |
   |                                                          |                                                                                                                                                                                             |
   | :ref:`Sound Classification <modelarts_23_0015>`          |                                                                                                                                                                                             |
   |                                                          |                                                                                                                                                                                             |
   | :ref:`Speech Labeling <modelarts_23_0016>`               |                                                                                                                                                                                             |
   |                                                          |                                                                                                                                                                                             |
   | :ref:`Speech Paragraph Labeling <modelarts_23_0017>`     |                                                                                                                                                                                             |
   |                                                          |                                                                                                                                                                                             |
   | :ref:`Video Labeling <modelarts_23_0282>`                |                                                                                                                                                                                             |
   +----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Import Operation <modelarts_23_0006>`              | Import the local manifest file or data stored in OBS to the dataset.                                                                                                                        |
   +----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Exporting Data <modelarts_23_0214>`                | Export part of the data as a new dataset or to OBS. Historical tasks can be viewed and managed.                                                                                             |
   +----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Modifying a Dataset <modelarts_23_0020>`           | Modify the basic information about a dataset, such as the dataset name, description, and labels.                                                                                            |
   +----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Publishing a Dataset <modelarts_23_0018>`          | Publish the labeled dataset as a new version for model building.                                                                                                                            |
   +----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Managing Dataset Versions <modelarts_23_0019>`     | View data version updates.                                                                                                                                                                  |
   +----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Introduction to Team Labeling <modelarts_23_0181>` | Allow multiple users to label the same dataset and enable the dataset creator to manage labeling tasks in a unified manner. Add a team and its members to participate in labeling datasets. |
   +----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Deleting a Dataset <modelarts_23_0021>`            | Delete a dataset to release resources.                                                                                                                                                      |
   +----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
