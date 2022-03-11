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

   +---------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Function                                                                                                | Description                                                                                                                                                                                 |
   +=========================================================================================================+=============================================================================================================================================================================================+
   | `Creating a Dataset <../data_management/creating_a_dataset.html>`__                                     | Create a dataset.                                                                                                                                                                           |
   +---------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | `Image Classification <../data_management/labeling_data/image_classification.html>`__                   | Label data based on the types of datasets. Data labeling is not supported for datasets in free format or table format.                                                                      |
   |                                                                                                         |                                                                                                                                                                                             |
   | `Object Detection <../data_management/labeling_data/object_detection.html>`__                           |                                                                                                                                                                                             |
   |                                                                                                         |                                                                                                                                                                                             |
   | `Text Classification <../data_management/labeling_data/text_classification.html>`__                     |                                                                                                                                                                                             |
   |                                                                                                         |                                                                                                                                                                                             |
   | `Named Entity Recognition <../data_management/labeling_data/named_entity_recognition.html>`__           |                                                                                                                                                                                             |
   |                                                                                                         |                                                                                                                                                                                             |
   | `Text Triplet <../data_management/labeling_data/text_triplet.html>`__                                   |                                                                                                                                                                                             |
   |                                                                                                         |                                                                                                                                                                                             |
   | `Sound Classification <../data_management/labeling_data/sound_classification.html>`__                   |                                                                                                                                                                                             |
   |                                                                                                         |                                                                                                                                                                                             |
   | `Speech Labeling <../data_management/labeling_data/speech_labeling.html>`__                             |                                                                                                                                                                                             |
   |                                                                                                         |                                                                                                                                                                                             |
   | `Speech Paragraph Labeling <../data_management/labeling_data/speech_paragraph_labeling.html>`__         |                                                                                                                                                                                             |
   |                                                                                                         |                                                                                                                                                                                             |
   | `Video Labeling <../data_management/labeling_data/video_labeling.html>`__                               |                                                                                                                                                                                             |
   +---------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | `Import Operation <../data_management/importing_data/import_operation.html>`__                          | Import the local manifest file or data stored in OBS to the dataset.                                                                                                                        |
   +---------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | `Exporting Data <../data_management/exporting_data.html>`__                                             | Export part of the data as a new dataset or to OBS. Historical tasks can be viewed and managed.                                                                                             |
   +---------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | `Modifying a Dataset <../data_management/modifying_a_dataset.html>`__                                   | Modify the basic information about a dataset, such as the dataset name, description, and labels.                                                                                            |
   +---------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | `Publishing a Dataset <../data_management/publishing_a_dataset.html>`__                                 | Publish the labeled dataset as a new version for model building.                                                                                                                            |
   +---------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | `Managing Dataset Versions <../data_management/managing_dataset_versions.html>`__                       | View data version updates.                                                                                                                                                                  |
   +---------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | `Introduction to Team Labeling <../data_management/team_labeling/introduction_to_team_labeling.html>`__ | Allow multiple users to label the same dataset and enable the dataset creator to manage labeling tasks in a unified manner. Add a team and its members to participate in labeling datasets. |
   +---------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | `Deleting a Dataset <../data_management/deleting_a_dataset.html>`__                                     | Delete a dataset to release resources.                                                                                                                                                      |
   +---------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+



.. |image1| image:: /_static/images/en-us_image_0000001156920919.png

