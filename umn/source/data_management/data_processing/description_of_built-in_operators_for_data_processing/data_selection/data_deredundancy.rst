:original_name: dataprocess-modelarts-00007.html

.. _dataprocess-modelarts-00007:

Data Deredundancy
=================

RRD Operator Overview
---------------------

The data with the largest difference can be removed based on the preset proportion.

.. table:: **Table 1** Advanced parameters

   +---------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Name          | Mandatory | Default | Description                                                                                                                                                                                                                  |
   +===============+===========+=========+==============================================================================================================================================================================================================================+
   | sample_ratio  | No        | 0.9     | Percentage of reserved data. The value ranges from 0 to 1. For example, **0.9** indicates that 90% of the original data is reserved.                                                                                         |
   +---------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | n_clusters    | auto      | auto    | Number of data sample types. The default value is **auto**, indicating that the total number of types is obtained based on the number of images in the directory. For example, you can specify the number of types to **4**. |
   +---------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | do_validation | No        | True    | Indicates whether to validate data. The value can be **True** or **False**. **True** indicates that data is validated before deredundancy. **False** indicates that data is deduplicated only.                               |
   +---------------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Operator Input Requirements
---------------------------

The following two types of operator input are available:

-  **Datasets**: Select a dataset and its version created on the ModelArts console from the drop-down list. Ensure that the dataset type be the same as the scenario type selected in this task.
-  **OBSCatalog**: Select either of the following storage structures:

   -  **Only images**: If the directory contains only images, the JPG, JPEG, PNG, and BMP formats are supported, and all images in the nested subdirectories are read.

   -  **Images and labels**: The structure varies depending on the scenario type.

      The following shows the directory structure in the image classification scenario. The following directory structure supports only single-label scenarios.

      .. code-block::

         input_path/
             --label1/
                 ----1.jpg
             --label2/
                 ----2.jpg
             --../

      The following shows the directory structure in the object detection scenario. Images in JPG, JPEG, PNG, and BMP formats are supported. XML files are standard PACAL VOC files.

      .. code-block::

         input_path/
             --1.jpg
             --1.xml
             --2.jpg
             --2.xml
             ...

Output Description
------------------

-  **Image classification**

   The output directory structure is as follows:

   .. code-block::

      output_path/
          --Data/
              ----class1/  # If the input data has labeling information, the information is also output. class1 indicates the labeling class.
                  ------1.jpg
              ----class2/
                  ------2.jpg
                  ------3.jpg
          --output.manifest

   A manifest file example is as follows:

   .. code-block::

      {
          "id": "xss",
          "source": "obs://home/fc8e2688015d4a1784dcbda44d840307_14.jpg",
          "usage": "train",
          "annotation": [
              {
                  "name": "Cat",
                  "type": "modelarts/image_classification"
              }
          ]
      }

-  **Object detection**

   The output directory structure is as follows:

   .. code-block::

      output_path/
          --Data/
              ----1.jpg
              ----1.xml  # If the input data has labeling information, the information is also output. xml indicates the label file.
              ----2.jpg
              ----3.jpg
          --output.manifest

   A manifest file example is as follows:

   .. code-block::

      {
          "source":"obs://fake/be462ea9c5abc09f.jpg",
          "annotation":[
              {
                  "annotation-loc":"obs://fake/be462ea9c5abc09f.xml",
                  "type":"modelarts/object_detection",
                  "annotation-format":"PASCAL VOC",
                  "annotated-by":"modelarts/hard_example_algo"
                  }
          ]
      }
