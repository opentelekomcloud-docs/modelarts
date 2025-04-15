:original_name: dataprepare-modelarts-0013.html

.. _dataprepare-modelarts-0013:

Specifications for Importing Data from an OBS Directory
=======================================================

When importing data from OBS, the data storage directory and file name must comply with the ModelArts specifications.

Only the following labeling types of data can be imported by **Labeling Format**: image classification, object detection, image segmentation, text classification, and sound classification.

.. note::

   -  To import data from an OBS directory, you must have the read permission on the OBS directory.
   -  The OBS buckets and ModelArts must be in the same region.

.. _en-us_topic_0000002233740360__en-us_topic_0000001194052681_section570816190577:

Image Classification
--------------------

Data for image classification can be stored in two formats:

Format 1: ModelArts imageNet 1.0

-  Images with the same label must be stored in the same directory, with the label name as the directory name. If there are multiple levels of directories, the last level is used as the label name.

   In the following example, **Rabbit** and **Panda** are label names.

   .. code-block::

      dataset-import-example
      ├─Rabbit
      │      10.jpg
      │      11.jpg
      │      12.jpg
      │
      └─Panda
              1.jpg
              2.jpg
              3.jpg

Format 2: ModelArts image classification 1.0

-  The image and labeled file must be stored in the same directory, with the content in the labeled file used as label names.

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

      Rabbit

   The following shows a label file for multiple labels, for example, the **2.txt** file:

   .. code-block::

      Rabbit
      Panda

-  Only images in JPG, JPEG, PNG, and BMP formats are supported. The size of a single image cannot exceed 5 MB, and the total size of all images uploaded at a time cannot exceed 8 MB.

Object Detection
----------------

Data for object detection can be stored in two formats:

Format 1: ModelArts PASCAL VOC 1.0

-  The simple mode of object detection requires you to store labeled objects and your label files (in one-to-one relationship with the labeled objects) in the same directory. For example, if the name of the labeled object file is **IMG_20180919_114745.jpg**, the name of the label file must be **IMG_20180919_114745.xml**.

   The label files must be in PASCAL VOC format. For details about the format, see :ref:`Table 8 <en-us_topic_0000002268739637__en-us_topic_0000001148092878_table77167388472>`.

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

-  Only images in JPG, JPEG, PNG, and BMP formats are supported. A single image cannot exceed 5 MB, and the total size of all images uploaded at a time cannot exceed 8 MB.

Format 2: YOLO

-  A YOLO dataset must comply with the following structure:

   .. code-block::

      └─ yolo_dataset/
         │
         ├── obj.names  # Label set file
         ├── obj.data   # Files and relative paths for recording dataset information
         ├── train.txt  # Relative path of images in the training set
         ├── valid.txt  # Relative path of images in the validation set
         │
         ├── obj_train_data/  # Directory where the images in the training set and the corresponding label files are stored
         │    ├── image1.txt  # BBox label list for image 1
         │    ├── image1.jpg
         │    ├── image2.txt
         │    ├── image2.jpg
         │    ├── ...
         │
         ├── obj_valid_data/  # Directory where the images in the validation set and the corresponding label files are stored
         │    ├── image101.txt
         │    ├── image101.jpg
         │    ├── image102.txt
         │    ├── image102.jpg
         │    ├── ...

   A YOLO dataset supports only training sets and validation sets. If other sets are imported, they will be invalid in the YOLO dataset.

-  The **obj.data** contains the following content and at least one of the **train** and **valid** subsets must be contained. The file paths are relative paths.

   .. code-block::

      classes = 5 # Optional
      names = <path/to/obj.names># For example, obj.names
      train = <path/to/train.txt># For example, train.txt
      valid = <path/to/valid.txt># Optional, for example, valid.txt
      backup = backup/ # Optional

-  The **obj.names** file records the label list. Each row label is used as the file index.

   .. code-block::

      label1 # index of label 1: 0
      label2 # index of label 2: 1
      label3
      ...

-  The file paths in **train.txt** and **valid.txt** are relative paths, and the file list must be in one-to-one relationship with the files in the directories. The file structures of the two files are as follows:

   .. code-block::

      <path/to/image1.jpg># For example, obj_train_data/image.jpg
      <path/to/image2.jpg># For example, obj_train_data/image.jpg
      ...

-  The .txt files in the **obj_train_data/** and **obj_valid_data/** directories contain the BBox label information of the corresponding images. Each line indicates a BBox label.

   .. code-block::

      # image1.txt:
      # <label_index> <x_center> <y_center> <width> <height>
      0 0.250000 0.400000 0.300000 0.400000
      3 0.600000 0.400000 0.400000 0.266667

   **x_center**, **y_center**, **width**, and **height** indicate the normalized parameters for the target bounding box: the x-coordinate and y-coordinate of the center point, width, and height.

-  Only images in JPG, JPEG, PNG, and BMP formats are supported. A single image cannot exceed 5 MB, and the total size of all images uploaded at one time cannot exceed 8 MB.

Image Segmentation
------------------

ModelArts image segmentation 1.0:

-  Labeled objects and their label files (in one-to-one relationship with the labeled objects) must be in the same directory. For example, if the name of the labeled object file is **IMG_20180919_114746.jpg**, the name of the label file must be **IMG_20180919_114746.xml**.

   Fields **mask_source** and **mask_color** are added to the label file in PASCAL VOC format. For details about the format, see :ref:`Table 4 <en-us_topic_0000002268739637__en-us_topic_0000001148092878_table1516151991311>`.

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
          <filename>image_0006.jpg</filename>
          <source>
              <database>Unknown</database>
          </source>
          <size>
              <width>230</width>
              <height>300</height>
              <depth>3</depth>
          </size>
          <segmented>1</segmented>
          <mask_source>obs://xianao/out/dataset-8153-Jmf5ylLjRmSacj9KevS/annotation/V001/segmentationClassRaw/image_0006.png</mask_source>
          <object>
              <name>bike</name>
              <pose>Unspecified</pose>
              <truncated>0</truncated>
              <difficult>0</difficult>
              <mask_color>193,243,53</mask_color>
              <occluded>0</occluded>
              <polygon>
                  <x1>71</x1>
                  <y1>48</y1>
                  <x2>75</x2>
                  <y2>73</y2>
                  <x3>49</x3>
                  <y3>69</y3>
                  <x4>68</x4>
                  <y4>92</y4>
                  <x5>90</x5>
                  <y5>101</y5>
                  <x6>45</x6>
                  <y6>110</y6>
                  <x7>71</x7>
                  <y7>48</y7>
              </polygon>
          </object>
      </annotation>

.. _en-us_topic_0000002233740360__en-us_topic_0000001194052681_section163641141195713:

Text Classification
-------------------

The TXT and CSV files can be imported for text classification, with the text encoding format of UTF-8 or GBK.

Labeled objects and labels for text classification can be stored in two formats:

-  ModelArts text classification combine 1.0: The labeled objects and labels for text classification are in the same text file. You can specify a separator to separate the labeled objects and labels, as well as multiple labels.

   For example, the following shows an example text file. The **Tab** key is used to separate the labeled objects from the labels.

   .. code-block::

      It touches good and responds quickly. I don't know how it performs in the future.   positive
      Three months ago, I bought a very good phone and replaced my old one with it. It can operate longer between charges.  positive
      Why does my phone heat up if I charge it for a while? The volume button stuck after being pressed down.  negative
      It's a gift for Father's Day. The delivery is fast and I received it in 24 hours. I like the earphones because the bass sounds feel good and they would not fall off.  positive

-  ModelArts text classification 1.0: The labeled objects and labels for text classification are text files, and correspond to each other based on the rows. For example, the first row in a label file indicates the label of the first row in the file of the labeled object.

   For example, the content of the labeled object **COMMENTS_20180919_114745.txt** is as follows:

   .. code-block::

      It touches good and responds quickly. I don't know how it performs in the future.
      I bought a phone three months ago and replaced the old phone with it. The standby time of the new phone is much better than that of the old one.
      Why does my phone heat up if I charge it for a while? The volume button stuck after being pressed down.
      It's a gift for Father's Day. The delivery is fast and I received it in 24 hours. I like the earphones because the bass sounds feel good and they would not fall off.

   The content of the label file **COMMENTS_20180919_114745_result.txt** is as follows:

   .. code-block::

      positive
      negative
      negative
      positive

   This data format requires you to store labeled objects and your label files (in one-to-one relationship with the labeled objects) in the same directory. For example, if the name of the labeled object file is **COMMENTS_20180919_114745.txt**, the name of the label file must be **COMMENTS \_20180919_114745_result.txt**.

   Example of data files:

   .. code-block::

      ├─dataset-import-example
      │      COMMENTS_20180919_114732.txt
      │      COMMENTS _20180919_114732_result.txt
      │      COMMENTS _20180919_114745.txt
      │      COMMENTS _20180919_114745_result.txt
      │      COMMENTS _20180919_114945.txt
      │      COMMENTS _20180919_114945_result.txt

.. _en-us_topic_0000002233740360__en-us_topic_0000001194052681_section1683314458578:

Sound Classification
--------------------

ModelArts audio classification dir 1.0: Sound files with the same label must be stored in the same directory, and the label name is the directory name.

Example:

.. code-block::

   dataset-import-example
   ├─Rabbit
   │      10.wav
   │      11.wav
   │      12.wav
   │
   └─Panda
           1.wav
           2.wav
           3.wav

.. _en-us_topic_0000002233740360__en-us_topic_0000001194052681_section118011361754:

Tables
------

CSV files can be imported from OBS. Select the directory where the files are stored. The number of columns in the CSV file must be the same as that in the dataset schema. The schema of the CSV file can be automatically obtained.

.. code-block::

   ├─dataset-import-example
   │      table_import_1.csv
   │      table_import_2.csv
   │      table_import_3.csv
   │      table_import_4.csv
