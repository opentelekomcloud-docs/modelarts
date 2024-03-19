:original_name: modelarts_23_0008.html

.. _modelarts_23_0008:

Specifications for Importing Data from an OBS Directory
=======================================================

When a dataset is imported, the data storage directory and file name must comply with the ModelArts specifications if the data to be used is stored in OBS.

Only the following types of dataset support the **OBS path** import mode: **Image classification**, **Object detection**, **Text classification**, **Table**, and **Sound classification**.

.. note::

   To import data from an OBS directory, you must have the read permission on the OBS directory.

.. _modelarts_23_0008__en-us_topic_0170886816_section570816190577:

Image Classification
--------------------

-  Image classification data can be in two modes. The first mode (directory mode) supports only single labels. The second mode (**.txt** label files) supports multiple labels.

   -  Images with the same label must be stored in the same directory, and the label name is the directory name. If there are multiple levels of directories, the last level is used as the label name.

      In the following example, **Cat** and **Rabbit** are label names.

      .. code-block::

         dataset-import-example
         ├─Cat
         │      10.jpg
         │      11.jpg
         │      12.jpg
         │
         └─Rabbit
                 1.jpg
                 2.jpg
                 3.jpg

   -  If **.txt** files exist in the directory, the content in the **.txt** files is used as the image label. This mode is better than the previous one.

      In the following example, **import-dir-1** and **import-dir-2** are the imported subdirectories:

      .. code-block::

         dataset-import-example
         ├─import-dir-1
         │      10.jpg
         │      10.txt
         │      11.jpg
         │      11.txt
         │      12.jpg
         │      12.txt
         └─import-dir-2
                 1.jpg
                 1.txt
                 2.jpg
                 2.txt

      The following shows a label file for a single label, for example, the **1.txt** file:

      .. code-block::

         Cat

      The following shows a label file for multiple labels, for example, the **1.txt** file:

      .. code-block::

         Cat
         Rabbit

-  Only images in JPG, JPEG, PNG, and BMP formats are supported. The size of a single image cannot exceed 5 MB, and the total size of all images uploaded at a time cannot exceed 8 MB.

.. _modelarts_23_0008__en-us_topic_0170886816_section1371122614572:

Object Detection
----------------

-  The simple mode of object detection requires users store labeled objects and their label files (in one-to-one relationship with the labeled objects) in the same directory. For example, if the name of the labeled object file is **IMG_20180919_114745.jpg**, the name of the label file must be **IMG_20180919_114745.xml**.

   The label files for object detection must be in PASCAL VOC format. For details about the format, see :ref:`Table 6 <modelarts_23_0009__en-us_topic_0170886817_table77167388472>`.

   Example:

   .. code-block::

      ├─dataset-import-example
      │      IMG_20180919_114732.jpg
      │      IMG_20180919_114732.xml
      │      IMG_20180919_114745.jpg
      │      IMG_20180919_114745.xml
      │      IMG_20180919_114945.jpg
      │      IMG_20180919_114945.xml

   A label file example is as follows:

   ::

      <?xml version="1.0" encoding="UTF-8" standalone="no"?>
      <annotation>
          <folder>NA</folder>
          <filename>bike_1_1593531469339.png</filename>
          <source>
              <database>Unknown</database>
          </source>
          <size>
              <width>554</width>
              <height>606</height>
              <depth>3</depth>
          </size>
          <segmented>0</segmented>
          <object>
              <name>Rabbit</name>
              <pose>Unspecified</pose>
              <truncated>0</truncated>
              <difficult>0</difficult>
              <occluded>0</occluded>
              <bndbox>
                  <xmin>279</xmin>
                  <ymin>52</ymin>
                  <xmax>474</xmax>
                  <ymax>278</ymax>
              </bndbox>
          </object>
          <object>
              <name>Cat</name>
              <pose>Unspecified</pose>
              <truncated>0</truncated>
              <difficult>0</difficult>
              <occluded>0</occluded>
              <bndbox>
                  <xmin>279</xmin>
                  <ymin>198</ymin>
                  <xmax>456</xmax>
                  <ymax>421</ymax>
              </bndbox>
          </object>
      </annotation>

-  Only images in JPG, JPEG, PNG, and BMP formats are supported. The size of a single image cannot exceed 5 MB, and the total size of all images uploaded at a time cannot exceed 8 MB.

.. _modelarts_23_0008__en-us_topic_0170886816_section163641141195713:

Text Classification
-------------------

txt and csv files can be imported for text classification, with the text encoding format of UTF-8 or GBK.

Labeled objects and labels for text classification can be stored in two modes:

-  The labeled objects and labels for text classification are in the same text file. You can specify a separator to separate the labeled objects and labels, as well as multiple labels.

   For example, the following shows an example text file. The **Tab** key is used to separate the labeled object from the label.

   .. code-block::

      It touches good and responds quickly. I don't know how it performs in the future.   positive
      Three months ago, I bought a very good phone and replaced my old one with it. It can operate longer between charges.  positive
      Why does my phone heat up if I charge it for a while? The volume button stuck after being pressed down.  negative
      It's a gift for Father's Day. The logistics is fast and I received it in 24 hours. I like the earphones because the bass sounds feel good and they would not fall off.  positive

-  The labeled objects and labels for text classification are text files, and correspond to each other based on the rows. For example, the first row in a label file indicates the label of the first row in the file of the labeled object.

   For example, the content of labeled object **COMMENTS_20180919_114745.txt** is as follows:

   .. code-block::

      It touches good and responds quickly. I don't know how it performs in the future.
      Three months ago, I bought a very good phone and replaced my old one with it. It can operate longer between charges.
      Why does my phone heat up if I charge it for a while? The volume button stuck after being pressed down.
      It's a gift for Father's Day. The logistics is fast and I received it in 24 hours. I like the earphones because the bass sounds feel good and they would not fall off.

   The content of label file **COMMENTS_20180919_114745_result.txt** is as follows:

   .. code-block::

      positive
      negative
      negative
      positive

   The data format requires users to store labeled objects and their label files (in one-to-one relationship with the labeled objects) in the same directory. For example, if the name of the labeled object file is **COMMENTS_20180919_114745.txt**, the name of the label file must be **COMMENTS \_20180919_114745_result.txt**.

   Example of data file storage:

   .. code-block::

      ├─dataset-import-example
      │      COMMENTS_20180919_114732.txt
      │      COMMENTS _20180919_114732_result.txt
      │      COMMENTS _20180919_114745.txt
      │      COMMENTS _20180919_114745_result.txt
      │      COMMENTS _20180919_114945.txt
      │      COMMENTS _20180919_114945_result.txt

.. _modelarts_23_0008__en-us_topic_0170886816_section1683314458578:

Sound Classification
--------------------

For sound classification, sound files with the same label must be stored in the same directory, and the label name is the directory name.

Example:

.. code-block::

   dataset-import-example
   ├─Cat
   │      10.wav
   │      11.wav
   │      12.wav
   │
   └─Rabbit
           1.wav
           2.wav
           3.wav
