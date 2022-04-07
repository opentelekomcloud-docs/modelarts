.. _modelarts_23_0067:

Viewing the Batch Service Prediction Result
===========================================

When deploying a batch service, you can select the location of the output data directory. You can view the running result of the batch service that is in the **Running completed** status.

Procedure
---------

#. Log in to the ModelArts management console and choose **Service Deployment** > **Batch Services**.
#. Click the name of the target service in the **Running completed** status. The service details page is displayed.

   -  You can view the service name, status, ID, input path, output path, and description.
   -  You can click |image1| in the **Description** area to edit the description.

#. Obtain the detailed OBS path next to **Output Path**, switch to the path and obtain the batch service prediction result.

   -  If images are entered, a result file is generated for each image in the *Image name*\ **\__result.txt** format, for example, **IMG_20180919_115016.jpg_result.txt**.
   -  If audio files are entered, a result file is generated for each audio file in the *Audio file name*\ **\__result.txt** format, for example, **1-36929-A-47.wav_result.txt**.
   -  If table data is entered, the result file is generated in the *Table name*\ **\__result.txt** format, for example, **train.csv_result.txt**.

.. |image1| image:: /_static/images/en-us_image_0000001157080919.png

