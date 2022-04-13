.. _modelarts_21_0003:

Preparing Data
==============

Before using ModelArts ExeML to build a model, upload data to an OBS bucket.

Uploading Data to OBS
---------------------

This operation uses the OBS console to upload data. For more information about how to create a bucket and upload files, see Creating a Bucket and Uploading an Object.

Perform the following operations to import data to the dataset for model training and building.

#. Log in to OBS Console and create a bucket.
#. Upload the local data to the OBS bucket. If you have a large amount of data, use OBS Browser+ to upload data or folders. The uploaded data must meet the dataset requirements of the ExeML project.

Requirements on Datasets
------------------------

-  The name of files in a dataset cannot contain Chinese characters, plus signs (+), spaces, or tabs.
-  Ensure that no damaged image exists. The supported image formats include JPG, JPEG, BMP, and PNG.
-  Do not store data of different projects in the same dataset.
-  Prepare sufficient data and balance each class of data. To achieve better results, prepare at least 100 images of each class in a training set for image classification.
-  To ensure the prediction accuracy of models, the training samples must be similar to the actual application scenarios.
-  To ensure the generalization capability of models, datasets should cover all possible scenarios.

Requirements for Files Uploaded to OBS
--------------------------------------

-  If you do not need to upload training data in advance, create an empty folder to store files generated in the future, for example, **/bucketName/data-cat**.
-  If you need to upload images to be labeled in advance, create an empty folder and save the images in the folder. An example of the image directory structure is **/bucketName/data-cat/cat.jpg**.
-  If you want to upload labeled images to the OBS bucket, upload them according to the following specifications:

   -  The dataset for image classification requires storing labeled objects and their label files (in one-to-one relationship with the labeled objects) in the same directory. For example, if the name of the labeled object is **10.jpg**, the name of the label file must be **10.txt**.

      Example of data files:

      .. code-block::

         ├─<dataset-import-path>
               │      10.jpg
               │      10.txt    
               │      11.jpg 
               │      11.txt
               │      12.jpg 
               │      12.txt

   -  Images in JPG, JPEG, PNG, and BMP formats are supported. When uploading images on the ModelArts management console, ensure that the size of an image does not exceed 5 MB and the total size of images to be uploaded in one attempt does not exceed 8 MB. If the data volume is large, use OBS Browser+ to upload images.

   -  A label name can contain a maximum of 32 characters, including Chinese characters, letters, digits, hyphens (-), and underscores (_).

   -  Image classification label file (**.txt**) rule:

      Each row contains only one label.

      .. code-block::

         cat
         dog
         ...
