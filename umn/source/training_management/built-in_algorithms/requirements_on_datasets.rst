:original_name: modelarts_23_0157.html

.. _modelarts_23_0157:

Requirements on Datasets
========================

The built-in algorithms provided by ModelArts can be used for image classification, object detection, and image semantic segmentation. The requirements for the datasets vary according to the built-in algorithms used for different purposes. Before using a built-in algorithm to create a training job, you are advised to prepare a dataset based on the requirements of the algorithm.

Image Classification
--------------------

The training dataset must be stored in the OBS bucket. The following shows the OBS path structure of the dataset:

.. code-block::

   |-- data_url
         |--a.jpg
         |--a.txt
         |--b.jpg
         |--b.txt
         ...

-  **data_url** indicates the folder name. You can customize the folder name. Images and label files cannot be stored in the root directory of an OBS bucket.

-  Images and label files must have the same name. The **.txt** files are label files for image classification. The images can be in JPG, JPEG, PNG, or BMP format.

-  The first row of label files for image classification indicates the category name of images, which can be Chinese characters, English letters, or digits. The following provides an example of file content:

   .. code-block::

      cat

-  In addition to the preceding files and folders, no other files or folders can exist in the **data_url** folder.

-  You can directly use an existing image classification dataset with published versions in **Data Management** of ModelArts.

-  You can also name sub-folders in the **data_url** directory by label, as shown in the following:

   .. code-block::

      |-- data_url
          |--cat
            |--a.jpg
            |--a.txt
          |--dog
            |--b.jpg
            |--b.txt
            ...

Object Detection and Locating
-----------------------------

The training dataset must be stored in the OBS bucket. The following shows the OBS path structure of the dataset:

.. code-block::

   |-- data_url
         |--a.jpg
         |--a.xml
         |--b.jpg
         |--b.xml
         ...

-  **data_url** indicates the folder name. You can customize the folder name. Images and label files cannot be stored in the root directory of an OBS bucket.
-  Images and label files must have the same name. The **.xml** files are label files for object detection. The images can be in JPG, JPEG, PNG, or BMP format.
-  In addition to the preceding files and folders, no other files or folders can exist in the **data_url** folder.
-  You can directly use an existing object detection dataset with published versions in **Data Management** of ModelArts.
-  The following provides a label file for object detection. The key parameters are **size** (image size), **object** (object information), and **name** (label name, which can be Chinese characters, English letters, or digits). Note that the values of **xmin**, **ymin**, **xmax**, and **ymax** in the **bndbox** field cannot exceed the value of **size**. That is, the value of **min** cannot be less than 0, and the value of **max** cannot be greater than the value of **width** or **height**.

   +-----------------------------------+-----------------------------------------------------------+
   | ::                                | ::                                                        |
   |                                   |                                                           |
   |     1                             |    <?xml version="1.0" encoding="UTF-8" standalone="no"?> |
   |     2                             |    <annotation>                                           |
   |     3                             |        <folder>Images</folder>                            |
   |     4                             |        <filename>IMG_20180919_120022.jpg</filename>       |
   |     5                             |        <source>                                           |
   |     6                             |            <database>Unknown</database>                   |
   |     7                             |        </source>                                          |
   |     8                             |        <size>                                             |
   |     9                             |            <width>800</width>                             |
   |    10                             |            <height>600</height>                           |
   |    11                             |            <depth>1</depth>                               |
   |    12                             |        </size>                                            |
   |    13                             |        <segmented>0</segmented>                           |
   |    14                             |        <object>                                           |
   |    15                             |            <name>yunbao</name>                            |
   |    16                             |            <pose>Unspecified</pose>                       |
   |    17                             |            <truncated>0</truncated>                       |
   |    18                             |            <difficult>0</difficult>                       |
   |    19                             |            <bndbox>                                       |
   |    20                             |                <xmin>216.00</xmin>                        |
   |    21                             |                <ymin>108.00</ymin>                        |
   |    22                             |                <xmax>705.00</xmax>                        |
   |    23                             |                <ymax>488.00</ymax>                        |
   |    24                             |            </bndbox>                                      |
   |    25                             |        </object>                                          |
   |    26                             |    </annotation>                                          |
   +-----------------------------------+-----------------------------------------------------------+

Image Semantic Segmentation
---------------------------

The training dataset must be stored in the OBS bucket. The following shows the OBS path structure of the dataset:

.. code-block::

   |-- data_url
          |--Image
                 |--a.jpg
                 |--b.jpg
                 ...
          |--Label
                 |--a.jpg
                 |--b.jpg
                 ...
          |--train.txt
          |--val.txt

**Description**:

-  **data_url**, **Image**, and **Label** indicate the OBS folder names. The **Image** folder stores images for semantic segmentation, and the **Label** folder stores labeled images.

-  The name and format of the images for semantic segmentation must be the same as those of the corresponding labeled images. Images in JPG, JPEG, PNG, and BMP formats are supported.

-  In the preceding code snippet, **train.txt** and **val.txt** are two list files. **train.txt** is the list file of the training set, and **val.txt** is the list file of the validation set. It is recommended that the ratio of the training set to the validation set be 8:2.

   In the list file, the relative paths of images and labels are separated by spaces. Different pieces of data are separated by newline characters. The following gives an example:

   .. code-block::

      Image/a.jpg Label/a.jpg
      Image/b.jpg Label/b.jpg
      ...
