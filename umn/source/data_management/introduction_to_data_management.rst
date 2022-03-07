Introduction to Data Management
===============================

In ModelArts, you can import and label data on the **Data Management** page to prepare for model building. ModelArts uses datasets as the basis for model development or training.

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

   -  Free format: manages data in any format. Labeling is not available for data of the free format type. The free format type is applicable to scenarios where labeling is not required or developers customize labeling. If your dataset needs to contain data in multiple formats or your data format does not meet the requirements of other types of datasets, you can select a dataset in free format.\ **Figure 1** Example of a dataset in free format
      |image1|

Dataset Management Process and Functions
----------------------------------------



.. _modelarts_23_0003__en-us_topic_0171496996_table145501032184813:

.. table:: **Table 1** Function description

   +-----------------------------------------------------------+-----------------------------------------------------------+
   | Function                                                  | Description                                               |
   +===========================================================+===========================================================+
   | `Creating a Dataset <modelarts_23_0004.html>`__           | Create a dataset.                                         |
   +-----------------------------------------------------------+-----------------------------------------------------------+
   | `Image Classification <modelarts_23_0011.html>`__         | Label data based on the types of datasets. Data labeling  |
   |                                                           | is not supported for datasets in free format or table     |
   | `Object Detection <modelarts_23_0012.html>`__             | format.                                                   |
   |                                                           |                                                           |
   | `Text Classification <modelarts_23_0013.html>`__          |                                                           |
   |                                                           |                                                           |
   | `Named Entity Recognition <modelarts_23_0014.html>`__     |                                                           |
   |                                                           |                                                           |
   | `Text Triplet <modelarts_23_0211.html>`__                 |                                                           |
   |                                                           |                                                           |
   | `Sound Classification <modelarts_23_0015.html>`__         |                                                           |
   |                                                           |                                                           |
   | `Speech Labeling <modelarts_23_0016.html>`__              |                                                           |
   |                                                           |                                                           |
   | `Speech Paragraph Labeling <modelarts_23_0017.html>`__    |                                                           |
   |                                                           |                                                           |
   | `Video Labeling <modelarts_23_0282.html>`__               |                                                           |
   +-----------------------------------------------------------+-----------------------------------------------------------+
   | `Import Operation <modelarts_23_0006.html>`__             | Import the local manifest file or data stored in OBS to   |
   |                                                           | the dataset.                                              |
   +-----------------------------------------------------------+-----------------------------------------------------------+
   | `Exporting Data <modelarts_23_0214.html>`__               | Export part of the data as a new dataset or to OBS.       |
   |                                                           | Historical tasks can be viewed and managed.               |
   +-----------------------------------------------------------+-----------------------------------------------------------+
   | `Modifying a Dataset <modelarts_23_0020.html>`__          | Modify the basic information about a dataset, such as the |
   |                                                           | dataset name, description, and labels.                    |
   +-----------------------------------------------------------+-----------------------------------------------------------+
   | `Publishing a Dataset <modelarts_23_0018.html>`__         | Publish the labeled dataset as a new version for model    |
   |                                                           | building.                                                 |
   +-----------------------------------------------------------+-----------------------------------------------------------+
   | `Managing Dataset Versions <modelarts_23_0019.html>`__    | View data version updates.                                |
   +-----------------------------------------------------------+-----------------------------------------------------------+
   | `Introduction to Team                                     | Allow multiple users to label the same dataset and enable |
   | Labeling <modelarts_23_0181.html>`__                      | the dataset creator to manage labeling tasks in a unified |
   |                                                           | manner. Add a team and its members to participate in      |
   |                                                           | labeling datasets.                                        |
   +-----------------------------------------------------------+-----------------------------------------------------------+
   | `Deleting a Dataset <modelarts_23_0021.html>`__           | Delete a dataset to release resources.                    |
   +-----------------------------------------------------------+-----------------------------------------------------------+


.. |image1| image:: /images/en-us_image_0000001156920919.png

