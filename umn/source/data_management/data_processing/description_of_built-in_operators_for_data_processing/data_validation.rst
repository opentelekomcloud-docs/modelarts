:original_name: dataprocess-modelarts-00003.html

.. _dataprocess-modelarts-00003:

Data Validation
===============

MetaValidation Operator Overview
--------------------------------

ModelArts data validation uses the MetaValidation operator and supports the following image formats: JPG, JPEG, BMP, and PNG. The object detection scenario supports the XML labeling format but does not support the non-rectangular box labeling format. The MetaValidation operator supports data validation for images and XML files.

.. table:: **Table 1** Image data validation

   +-------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | Exception                                                                                             | Solution                                                                      |
   +=======================================================================================================+===============================================================================+
   | The images are damaged and cannot be decoded.                                                         | Filters out images that cannot be decoded.                                    |
   +-------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | The image channel can be channel 1 or channel 2. Channel 3 is not commonly used.                      | Converts images into RGB three-channel images.                                |
   +-------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | The image format is not supported by ModelArts.                                                       | Converts the image format to JPG.                                             |
   +-------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | The image suffix is inconsistent with the actual format, but the format is supported by ModelArts.    | Coverts the suffix to the actual format.                                      |
   +-------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | The image suffix is inconsistent with the actual format and the format is not supported by ModelArts. | Converts the image format to JPG.                                             |
   +-------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | The image resolution is too high.                                                                     | The image width and height are cropped based on the specified size and ratio. |
   +-------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------+

.. table:: **Table 2** Labeling file data validation

   +------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Exception                                                                                                        | Solution                                                                                                                      |
   +==================================================================================================================+===============================================================================================================================+
   | The XML structure is incomplete and cannot be parsed.                                                            | Filters XML files.                                                                                                            |
   +------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | No labeled object is in the XML file.                                                                            | Filters XML files.                                                                                                            |
   +------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | The XML file does not contain rectangle **bndbox**.                                                              | Filters XML files.                                                                                                            |
   +------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Some labeled objects do not have rectangle **bndbox**.                                                           | Filters labeled objects.                                                                                                      |
   +------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | After an image is cropped, the width and height of the image are inconsistent with those in the XML file.        | Changes the values of the width and height parameters to the actual width and height of the image.                            |
   +------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | No **width** and **height** fields exist in XML files.                                                           | Supplements the **width** and **height** fields and values in the XML file based on the actual width and height of the image. |
   +------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | After an image is cropped, its size is inconsistent with the size of rectangle **bndbox** in the XML file.       | Changes the value of **bndbox** in the XML file based on the image cropping ratio.                                            |
   +------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | The width or height of rectangle **bndbox** in the XML file is too small and is displayed as a line.             | If the difference between the width and height of the rectangle is less than 2, removes the current object.                   |
   +------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | In the XML file, the minimum value of rectangle **bndbox** is greater than the maximum value.                    | Removes the current object.                                                                                                   |
   +------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Rectangle **bndbox** exceeds the image boundaries, and the excess part occupies more than 50% of the frame area. | Removes the current object.                                                                                                   |
   +------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Rectangle **bndbox** exceeds the image boundaries, and the excess part occupies less than 50% of the frame area. | Rectangle **bndbox** is pulled back to the image boundaries.                                                                  |
   +------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+

.. note::

   Original data is not changed during data validation. The newly validated image or XML file is saved in the specified output path.

Parameters
----------

.. table:: **Table 3** Parameters of the MetaValidation operator for data validation

   +------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Name             | Mandatory       | Default         | Description                                                                                                                                                 |
   +==================+=================+=================+=============================================================================================================================================================+
   | image_max_width  | No              | -1              | Maximum width of an input image. If the width of an input image exceeds the configured value, the image is cropped based on the ratio. The unit is pixel.   |
   |                  |                 |                 |                                                                                                                                                             |
   |                  |                 |                 | The default value **-1** indicates that the image is not cropped.                                                                                           |
   +------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | image_max_height | No              | -1              | Maximum length of an input image. If the length of an input image exceeds the configured value, the image is cropped based on the ratio. The unit is pixel. |
   |                  |                 |                 |                                                                                                                                                             |
   |                  |                 |                 | The default value **-1** indicates that the image is not cropped.                                                                                           |
   +------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+

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
                  ------2_checked.jpg
              ----class2/
                  ------3.jpg
                  ------4_checked.jpg
              ----5_checked.jpg
          --output.manifest

   A manifest file example is as follows: The validation attribute **"property":{"@modelarts:data_checked":true}** is added for each data record.

   .. code-block::

      {
        "id": "xss",
        "source": "obs://hard_example_path/Data/fc8e2688015d4a1784dcbda44d840307_14_checked.jpg",
        "property": {
          "@modelarts:data_checked": true
        },
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
              ----1_checked.jpg
               ----1_checked.xml # If the input data is converted during validation, '_checked' is added to the file name.
              ----2.jpg          # If the input data is not converted, the file is saved with the original name.
              ----2.xml
         --output.manifest

   A manifest file example is as follows: The validation attribute **"property":{"@modelarts:data_checked":true}** is added for each data record.

   .. code-block::

      {
        "source": "obs://hard_example_path/Data/be462ea9c5abc09f_checked.jpg",
        "property": {
          "@modelarts:data_checked": true
        },
        "annotation": [
          {
            "annotation-loc": "obs://hard_example_path/Data/be462ea9c5abc09f_checked.xml",
            "type": "modelarts/object_detection",
            "annotation-format": "PASCAL VOC",
            "annotated-by": "modelarts/hard_example_algo"
          }
        ]
      }
