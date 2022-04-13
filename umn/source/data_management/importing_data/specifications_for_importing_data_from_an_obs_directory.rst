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

      In the following example, **Cat** and **Dog** are label names.

      .. code-block::

         dataset-import-example 
         ├─Cat 
         │      10.jpg 
         │      11.jpg 
         │      12.jpg 
         │ 
         └─Dog 
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
         Dog

-  Only images in JPG, JPEG, PNG, and BMP formats are supported. The size of a single image cannot exceed 5 MB, and the total size of all images uploaded at a time cannot exceed 8 MB.

.. _modelarts_23_0008__en-us_topic_0170886816_section1371122614572:

Object Detection
----------------

-  The simple mode of object detection requires users store labeled objects and their label files (in one-to-one relationship with the labeled objects) in the same directory. For example, if the name of the labeled object file is **IMG_20180919_114745.jpg**, the name of the label file must be **IMG_20180919_114745.xml**.

   The label files for object detection must be in PASCAL VOC format. For details about the format, see :ref:`Table 8 <modelarts_23_0009__en-us_topic_0170886817_table77167388472>`.

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

   +-----------------------------------+-----------------------------------------------------------+
   | ::                                | ::                                                        |
   |                                   |                                                           |
   |     1                             |    <?xml version="1.0" encoding="UTF-8" standalone="no"?> |
   |     2                             |    <annotation>                                           |
   |     3                             |        <folder>NA</folder>                                |
   |     4                             |        <filename>bike_1_1593531469339.png</filename>      |
   |     5                             |        <source>                                           |
   |     6                             |            <database>Unknown</database>                   |
   |     7                             |        </source>                                          |
   |     8                             |        <size>                                             |
   |     9                             |            <width>554</width>                             |
   |    10                             |            <height>606</height>                           |
   |    11                             |            <depth>3</depth>                               |
   |    12                             |        </size>                                            |
   |    13                             |        <segmented>0</segmented>                           |
   |    14                             |        <object>                                           |
   |    15                             |            <name>Dog</name>                               |
   |    16                             |            <pose>Unspecified</pose>                       |
   |    17                             |            <truncated>0</truncated>                       |
   |    18                             |            <difficult>0</difficult>                       |
   |    19                             |            <occluded>0</occluded>                         |
   |    20                             |            <bndbox>                                       |
   |    21                             |                <xmin>279</xmin>                           |
   |    22                             |                <ymin>52</ymin>                            |
   |    23                             |                <xmax>474</xmax>                           |
   |    24                             |                <ymax>278</ymax>                           |
   |    25                             |            </bndbox>                                      |
   |    26                             |        </object>                                          |
   |    27                             |        <object>                                           |
   |    28                             |            <name>Cat</name>                               |
   |    29                             |            <pose>Unspecified</pose>                       |
   |    30                             |            <truncated>0</truncated>                       |
   |    31                             |            <difficult>0</difficult>                       |
   |    32                             |            <occluded>0</occluded>                         |
   |    33                             |            <bndbox>                                       |
   |    34                             |                <xmin>279</xmin>                           |
   |    35                             |                <ymin>198</ymin>                           |
   |    36                             |                <xmax>456</xmax>                           |
   |    37                             |                <ymax>421</ymax>                           |
   |    38                             |            </bndbox>                                      |
   |    39                             |        </object>                                          |
   |    40                             |    </annotation>                                          |
   +-----------------------------------+-----------------------------------------------------------+

-  Only images in JPG, JPEG, PNG, and BMP formats are supported. The size of a single image cannot exceed 5 MB, and the total size of all images uploaded at a time cannot exceed 8 MB.

.. _modelarts_23_0008__en-us_topic_0170886816_section1363851815518:

Image Segmentation
------------------

-  The simple mode of image segmentation requires users store labeled objects and their label files (in one-to-one relationship with the labeled objects) in the same directory. For example, if the name of the labeled object file is **IMG_20180919_114746.jpg**, the name of the label file must be **IMG_20180919_114746.xml**.

   Fields **mask_source** and **mask_color** are added to the label file in PASCAL VOC format. For details about the format, see :ref:`Table 4 <modelarts_23_0009__en-us_topic_0170886817_table1516151991311>`.

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

   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | ::                                | ::                                                                                                                                      |
   |                                   |                                                                                                                                         |
   |     1                             |    <?xml version="1.0" encoding="UTF-8" standalone="no"?>                                                                               |
   |     2                             |    <annotation>                                                                                                                         |
   |     3                             |        <folder>NA</folder>                                                                                                              |
   |     4                             |        <filename>image_0006.jpg</filename>                                                                                              |
   |     5                             |        <source>                                                                                                                         |
   |     6                             |            <database>Unknown</database>                                                                                                 |
   |     7                             |        </source>                                                                                                                        |
   |     8                             |        <size>                                                                                                                           |
   |     9                             |            <width>230</width>                                                                                                           |
   |    10                             |            <height>300</height>                                                                                                         |
   |    11                             |            <depth>3</depth>                                                                                                             |
   |    12                             |        </size>                                                                                                                          |
   |    13                             |        <segmented>1</segmented>                                                                                                         |
   |    14                             |        <mask_source>obs://xianao/out/dataset-8153-Jmf5ylLjRmSacj9KevS/annotation/V001/segmentationClassRaw/image_0006.png</mask_source> |
   |    15                             |        <object>                                                                                                                         |
   |    16                             |            <name>bike</name>                                                                                                            |
   |    17                             |            <pose>Unspecified</pose>                                                                                                     |
   |    18                             |            <truncated>0</truncated>                                                                                                     |
   |    19                             |            <difficult>0</difficult>                                                                                                     |
   |    20                             |            <mask_color>193,243,53</mask_color>                                                                                          |
   |    21                             |            <occluded>0</occluded>                                                                                                       |
   |    22                             |            <polygon>                                                                                                                    |
   |    23                             |                <x1>71</x1>                                                                                                              |
   |    24                             |                <y1>48</y1>                                                                                                              |
   |    25                             |                <x2>75</x2>                                                                                                              |
   |    26                             |                <y2>73</y2>                                                                                                              |
   |    27                             |                <x3>49</x3>                                                                                                              |
   |    28                             |                <y3>69</y3>                                                                                                              |
   |    29                             |                <x4>68</x4>                                                                                                              |
   |    30                             |                <y4>92</y4>                                                                                                              |
   |    31                             |                <x5>90</x5>                                                                                                              |
   |    32                             |                <y5>101</y5>                                                                                                             |
   |    33                             |                <x6>45</x6>                                                                                                              |
   |    34                             |                <y6>110</y6>                                                                                                             |
   |    35                             |                <x7>71</x7>                                                                                                              |
   |    36                             |                <y7>48</y7>                                                                                                              |
   |    37                             |            </polygon>                                                                                                                   |
   |    38                             |        </object>                                                                                                                        |
   |    39                             |    </annotation>                                                                                                                        |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+

.. _modelarts_23_0008__en-us_topic_0170886816_section163641141195713:

Text Classification
-------------------

Text classification supports two import modes.

-  The labeled objects and labels for text classification are in the same text file. You can specify a separator to separate the labeled objects and labels, as well as multiple labeled objects.

   For example, the following shows an example text file. The **Tab** key is used to separate the labeled object from the label.

   .. code-block::

      It touches good and responds quickly. I don't know how it performs in the future.   positive
      Three months ago, I bought a very good phone and replaced my old one with it. It can operate longer between charges.  positive
      Why does my phone heat up if I charge it for a while? The volume button stuck after being pressed down.  negative
      It's a gift for Father's Day. The logistics is fast and I received it in 24 hours. I like the earphones because the bass sounds feel good and they would not fall off.  positive

-  The labeled objects and label files for text classification are text files, and correspond to each other based on the rows. For example, the first row in a label file indicates the label of the first row in the file of the labeled object.

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
   └─Dog 
           1.wav 
           2.wav 
           3.wav

.. _modelarts_23_0008__en-us_topic_0170886816_section1171862514918:

Table
-----

You can import data from OBS.

Import description:

#. The prerequisite for successful import is that the schema of the data source must be the same as that specified during dataset creation. The schema indicates column names and types of a table. Once specified during dataset creation, the values cannot be changed.
#. If the data format is invalid, the data is set to null values. For details, see :ref:`Table 4 <modelarts_23_0004__en-us_topic_0170886809_table1916832104917>`.
#. When a CSV file is imported from OBS, the data type is not verified, but the number of columns must be the same as that in the schema of the dataset.

-  From OBS

   CSV files can be imported from OBS. You need to select the directory where the files are stored. The number of columns in the CSV file must be the same as that in the dataset schema. The schema of the CSV file can be automatically obtained.

   .. code-block::

      ├─dataset-import-example 
      │      table_import_1.csv 
      │      table_import_2.csv
      │      table_import_3.csv
      │      table_import_4.csv
