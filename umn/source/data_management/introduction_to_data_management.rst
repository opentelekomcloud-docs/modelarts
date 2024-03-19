:original_name: modelarts_23_0003.html

.. _modelarts_23_0003:

Introduction to Data Management
===============================

In ModelArts, you can import and label data on the **Data Management** page to prepare for model building. ModelArts uses datasets as the basis for model development or training.

.. _modelarts_23_0003__en-us_topic_0171496996_section51771731153811:

Dataset Types
-------------

ModelArts supports datasets of images, audio, text, videos, and other types for the following purposes:

-  Images

   -  Image classification: identifies a class of objects in images.
   -  Object detection: identifies the position and class of each object in an image.

-  Audio

   -  Sound classification: classifies and identifies different sounds.
   -  Speech labeling: labels speech content.
   -  Speech paragraph labeling: segments and labels speech content.

-  Text

   -  Text classification: assigns labels to text according to its content.
   -  Named entity recognition: assigns labels to named entities in text, such as time and locations.
   -  Text triplet: assigns labels to entity segments and entity relationships in the text.

-  Videos

   -  Video labeling: identifies the position and class of each object in a video. Only the MP4 format is supported.

-  Others

   -  Free format: manages data in any format. Labeling is not available for data of the free format type. The free format type applies to scenarios where labeling is not required or developers customize labeling. Select this format if your data is in multiple formats or your data is not in any of the preceding formats.

Size Limit
----------

-  A video, text, or audio dataset can have a maximum size of 5 GB.
-  For an image dataset for object detection, image classification, or image segmentation, a single image can have a maximum size of 25 MB.
-  A manifest file can have a maximum size of 5 GB.
-  The maximum size of a line in a text file is 100 KB.
-  A data labeling result file can have a maximum size of 100 MB.

Dataset Management Process and Functions
----------------------------------------

.. table:: **Table 1** Function description

   +------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   | Function                                             | Description                                                                                                            |
   +======================================================+========================================================================================================================+
   | :ref:`Creating a Dataset <modelarts_23_0004>`        | Create a dataset.                                                                                                      |
   +------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Image Classification <modelarts_23_0011>`      | Label data based on the types of datasets. Data labeling is not supported for datasets in free format or table format. |
   |                                                      |                                                                                                                        |
   | :ref:`Object Detection <modelarts_23_0012>`          |                                                                                                                        |
   |                                                      |                                                                                                                        |
   | :ref:`Text Classification <modelarts_23_0013>`       |                                                                                                                        |
   |                                                      |                                                                                                                        |
   | :ref:`Named Entity Recognition <modelarts_23_0014>`  |                                                                                                                        |
   |                                                      |                                                                                                                        |
   | :ref:`Text Triplet <modelarts_23_0211>`              |                                                                                                                        |
   |                                                      |                                                                                                                        |
   | :ref:`Sound Classification <modelarts_23_0015>`      |                                                                                                                        |
   |                                                      |                                                                                                                        |
   | :ref:`Speech Labeling <modelarts_23_0016>`           |                                                                                                                        |
   |                                                      |                                                                                                                        |
   | :ref:`Speech Paragraph Labeling <modelarts_23_0017>` |                                                                                                                        |
   |                                                      |                                                                                                                        |
   | :ref:`Video Labeling <modelarts_23_0282>`            |                                                                                                                        |
   +------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Import Operation <modelarts_23_0006>`          | Import data to the dataset.                                                                                            |
   +------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Exporting Data <modelarts_23_0214>`            | Export part of the data as a new dataset or to OBS. Historical tasks can be viewed and managed.                        |
   +------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Modifying a Dataset <modelarts_23_0020>`       | Modify the basic information about a dataset, such as the dataset name, description, and labels.                       |
   +------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Publishing a Dataset <modelarts_23_0018>`      | Publish the labeled dataset as a new version for model building.                                                       |
   +------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Managing Dataset Versions <modelarts_23_0019>` | View data version updates.                                                                                             |
   +------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Deleting a Dataset <modelarts_23_0021>`        | Delete a dataset to release resources.                                                                                 |
   +------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
