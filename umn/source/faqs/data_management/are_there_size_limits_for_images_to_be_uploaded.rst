:original_name: modelarts_05_0102.html

.. _modelarts_05_0102:

Are There Size Limits for Images to be Uploaded?
================================================

For data management, there are limits on the image size when you upload images to the datasets whose labeling type is object detection or image classification. The size of an image cannot exceed 8 MB, and only JPG, JPEG, PNG, and BMP formats are supported.

**Solutions**:

-  Import the images from OBS. Upload images to any OBS directory and import the images from the OBS directory to an existing dataset.
-  Use data source synchronization. Upload images to the input directory or its subdirectory of a dataset, and click **Synchronize Data Source** on the dataset details page to add new images. Note that synchronizing a data source will delete the files deleted from OBS from the dataset. Exercise caution when performing this operation.
-  Create a dataset. Upload images to any OBS directory. You can directly use the image directory as the input directory to create the dataset.
