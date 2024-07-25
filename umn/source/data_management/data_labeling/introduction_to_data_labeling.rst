:original_name: datalabel-modelarts_0002.html

.. _datalabel-modelarts_0002:

Introduction to Data Labeling
=============================

Model training requires a large amount of labeled data. Therefore, before training a model, label data. ModelArts offers data labeling functions to assist with this process.

Manual Labeling
---------------

Create a labeling job based on the dataset type. ModelArts supports the following types of labeling jobs:

-  Image

   -  Image classification: identifies a class of objects in images.
   -  Object detection: identifies the position and class of each object in an image.
   -  Image segmentation: segments an image into different areas based on objects in the image.

-  Audio

   -  Sound classification: classifies and identifies different sounds.
   -  Speech labeling: labels speech content.
   -  Speech paragraph labeling: segments and labels speech content.

-  Text

   -  Text classification: assigns labels to text according to its content.
   -  Named entity recognition: assigns labels to named entities in text, such as time and locations.
   -  Text triplet: assigns labels to entity segments and entity relationships in the text.

-  Video

   Video labeling: identifies the position and class of each object in a video. Only the MP4 format is supported.

Dataset Functions
-----------------

Dataset functions vary depending on dataset types. For details, see :ref:`Table 1 <en-us_topic_0000001943986853__table475114812297>`.

.. _en-us_topic_0000001943986853__table475114812297:

.. table:: **Table 1** Functions supported by different types of datasets

   ============ ========================= ===============
   Dataset Type Labeling Type             Manual Labeling
   ============ ========================= ===============
   Image        Image classification      Yes
   \            Object detection          Yes
   \            Image segmentation        Yes
   Audio        Sound classification      Yes
   \            Speech Labeling           Yes
   \            Speech Paragraph Labeling Yes
   Text         Text classification       Yes
   \            Named entity recognition  Yes
   \            Text Triplet              Yes
   Videos       Video Labeling            Yes
   Free format  ``-``                     ``-``
   Table        ``-``                     ``-``
   ============ ========================= ===============
