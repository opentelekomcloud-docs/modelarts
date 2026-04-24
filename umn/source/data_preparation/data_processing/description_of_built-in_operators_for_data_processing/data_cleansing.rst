:original_name: dataprocess-modelarts-00004.html

.. _dataprocess-modelarts-00004:

Data Cleansing
==============

PCC Operator Overview
---------------------

ModelArts data cleansing is implemented by the PCC operator. The dataset used for image classification or object detection may contain images that do not belong to the required categories. These images need to be removed to avoid interference to labeling and model training.

Description
-----------

.. table:: **Table 1** Parameters of the PCC operator for data cleansing

   +-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Name                  | Mandatory       | Default         | Description                                                                                                                                                                                                                                                                                   |
   +=======================+=================+=================+===============================================================================================================================================================================================================================================================================================+
   | prototype_sample_path | Yes             | None            | Directory for storing positive data cleansing samples. The directory stores positive sample image files. The algorithm filters input data based on the positive sample images. That is, the data that is highly similar to the images in the **prototype_sample_path** directory is retained. |
   |                       |                 |                 |                                                                                                                                                                                                                                                                                               |
   |                       |                 |                 | Enter an existing OBS directory. The directory contains the provided positive sample images and starts with **obs://**, for example, *obs://obs_bucket_name/folder_name*.                                                                                                                     |
   +-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | criticism_sample_path | No              | None            | Directory for storing negative data cleansing samples. The directory stores negative sample image files. The algorithm filters input data based on the negative sample images. That is, the data that is less similar to the images in the **criticism_sample_path** directory is retained.   |
   |                       |                 |                 |                                                                                                                                                                                                                                                                                               |
   |                       |                 |                 | It is recommended that this parameter be used together with **prototype_sample_path** to improve the accuracy of data cleansing.                                                                                                                                                              |
   |                       |                 |                 |                                                                                                                                                                                                                                                                                               |
   |                       |                 |                 | Enter an existing OBS directory that starts with **obs://**, for example, *obs://obs_bucket_name/folder_name*.                                                                                                                                                                                |
   +-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | n_clusters            | No              | auto            | Number of data sample types. The default value is **auto**. You can enter an integer less than the total number of samples or **auto**. **auto** indicates that the number of images in the positive sample directory is used as the number of data sample types.                             |
   +-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | simlarity_threshold   | No              | 0.9             | Similarity threshold. If the similarity between two images exceeds the threshold, the two images are regarded as similar. Otherwise, they are regarded as dissimilar. The value ranges from 0 to 1.                                                                                           |
   +-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | embedding_distance    | No              | 0.2             | Distance between sample features. If the feature distance between two images is smaller than the specified value, the two images are regarded as similar. Otherwise, the two images are regarded as dissimilar. The value ranges from 0 to 1.                                                 |
   +-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | do_validation         | No              | True            | Indicates whether to validate data. The value can be **True** or **False**. **True** indicates that data is validated before cleansing. **False** indicates that data is cleansed only.                                                                                                       |
   +-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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
              ----3.jpg
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
