:original_name: modelarts_21_0063.html

.. _modelarts_21_0063:

Are There Size Limits for Images to be Uploaded?
================================================

For the data management function, there are limits on the image size when you upload images to the datasets whose labeling type is object detection or image classification. The size of an image cannot exceed 8 MB. Only JPG, JPEG, PNG, and BMP formats are supported.

Note that for the ExeML function, the size of an image to be uploaded cannot exceed 5 MB.

**Solutions**:

-  Method 1: Use the import function. Upload images to any OBS directory and import the images from the OBS directory to an existing dataset.
-  Method 2: Use the data source synchronization function. Upload images to the input directory or its subdirectory of a dataset, and click **Synchronize Data Source** on the dataset details page to add new images. Note that synchronizing a data source will delete the files deleted from OBS from the dataset. Exercise caution when performing this operation.
-  Method 3: Create a dataset. Upload images to any OBS directory. You can directly use the image directory as the input directory to create the dataset.
