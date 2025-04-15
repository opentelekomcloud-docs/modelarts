:original_name: dataprepare-modelarts-0005.html

.. _dataprepare-modelarts-0005:

Dataset Overview
================

Dataset Types
-------------

ModelArts supports the following types of datasets:

-  Images: in .jpg, .png, .jpeg, or .bmp format for image classification, image segmentation, and object detection
-  Audio: in .wav format for sound classification, speech labeling, and speech paragraph labeling
-  Text: in .txt or .csv format for text classification, named entity recognition, and text triplet labeling
-  Video: in .mp4 format for video labeling
-  Free format: allows data in any format. Labeling is not available for free format data. The free format applies if labeling is not required or needs to be customized. Select this format if your data is in multiple formats or your data is not in any of the preceding formats.

Dataset Functions
-----------------

Different types of datasets support different functions, such as auto labeling and team labeling. For details, see :ref:`Table 1 <en-us_topic_0000002233740336__table138425481245>`.

.. _en-us_topic_0000002233740336__table138425481245:

.. table:: **Table 1** Functions supported by different types of datasets

   +--------------+---------------------------+--------------------+----------------+----------------+----------------------+---------------------+---------------------------+---------------+---------------+
   | Dataset Type | Labeling Type             | Creating a Dataset | Importing Data | Exporting Data | Publishing a Dataset | Modifying a Dataset | Managing Dataset Versions | Auto Grouping | Data Features |
   +==============+===========================+====================+================+================+======================+=====================+===========================+===============+===============+
   | Image        | Image classification      | Supported          | Supported      | Supported      | Supported            | Supported           | Supported                 | Supported     | Supported     |
   +--------------+---------------------------+--------------------+----------------+----------------+----------------------+---------------------+---------------------------+---------------+---------------+
   |              | Object detection          | Supported          | Supported      | Supported      | Supported            | Supported           | Supported                 | Supported     | Supported     |
   +--------------+---------------------------+--------------------+----------------+----------------+----------------------+---------------------+---------------------------+---------------+---------------+
   |              | Image segmentation        | Supported          | Supported      | Supported      | Supported            | Supported           | Supported                 | Supported     | N/A           |
   +--------------+---------------------------+--------------------+----------------+----------------+----------------------+---------------------+---------------------------+---------------+---------------+
   | Audio        | Sound classification      | Supported          | Supported      | N/A            | Supported            | Supported           | Supported                 | N/A           | N/A           |
   +--------------+---------------------------+--------------------+----------------+----------------+----------------------+---------------------+---------------------------+---------------+---------------+
   |              | Speech labeling           | Supported          | Supported      | N/A            | Supported            | Supported           | Supported                 | N/A           | N/A           |
   +--------------+---------------------------+--------------------+----------------+----------------+----------------------+---------------------+---------------------------+---------------+---------------+
   |              | Speech paragraph labeling | Supported          | Supported      | N/A            | Supported            | Supported           | Supported                 | N/A           | N/A           |
   +--------------+---------------------------+--------------------+----------------+----------------+----------------------+---------------------+---------------------------+---------------+---------------+
   | Text         | Text classification       | Supported          | Supported      | N/A            | Supported            | Supported           | Supported                 | N/A           | N/A           |
   +--------------+---------------------------+--------------------+----------------+----------------+----------------------+---------------------+---------------------------+---------------+---------------+
   |              | Named entity recognition  | Supported          | Supported      | N/A            | Supported            | Supported           | Supported                 | N/A           | N/A           |
   +--------------+---------------------------+--------------------+----------------+----------------+----------------------+---------------------+---------------------------+---------------+---------------+
   |              | Text triplet              | Supported          | Supported      | N/A            | Supported            | Supported           | Supported                 | N/A           | N/A           |
   +--------------+---------------------------+--------------------+----------------+----------------+----------------------+---------------------+---------------------------+---------------+---------------+
   | Video        | Video labeling            | Supported          | Supported      | N/A            | Supported            | Supported           | Supported                 | N/A           | N/A           |
   +--------------+---------------------------+--------------------+----------------+----------------+----------------------+---------------------+---------------------------+---------------+---------------+
   | Free format  | Free format               | Supported          | N/A            | \_             | Supported            | Supported           | Supported                 | N/A           | N/A           |
   +--------------+---------------------------+--------------------+----------------+----------------+----------------------+---------------------+---------------------------+---------------+---------------+
   | Table        | Table                     | Supported          | Supported      | N/A            | Supported            | Supported           | Supported                 | N/A           | N/A           |
   +--------------+---------------------------+--------------------+----------------+----------------+----------------------+---------------------+---------------------------+---------------+---------------+

Specifications Restrictions
---------------------------

-  The maximum numbers of samples and labels in a single text, video, or audio database other than a table dataset are 1,000,000 and 10,000, respectively.
-  The maximum size of a sample in a single text, video, or audio database other than an image dataset is 5 GB.
-  The maximum size of an image for object detection, image segmentation, or image classification is 25 MB.
-  The maximum size of a manifest file is 5 GB.
-  The maximum size of a text file in a line is 100 KB.
-  The maximum size of a labeling result file is 100 MB.
