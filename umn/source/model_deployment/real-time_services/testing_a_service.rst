.. _modelarts_23_0062:

Testing a Service
=================

After a model is deployed as a real-time service, you can debug code or add files for testing on the **Prediction** tab page. Based on the input request (JSON text or file) defined by the model, the service can be tested in either of the following ways:

#. :ref:`JSON Text Prediction <modelarts_23_0062__en-us_topic_0165025306_section15840106121611>`: If the input type of the model of the deployed service is JSON text, that is, the input does not contain files, you can enter the JSON code on the **Prediction** tab page for service testing.
#. :ref:`File Prediction (Images and Audios) <modelarts_23_0062__en-us_topic_0165025306_section1666533761611>`: If the input type of the model of the deployed service is file, including images, audios, and videos, you can add images on the **Prediction** tab page for service testing.

.. note::

   -  If the input type is image, the size of a single image must be less than 10 MB.
   -  The following image types are supported: png, psd, jpg, jpeg, bmp, gif, webp, psd, svg, and tiff.

Input Parameters
----------------

For the service that you have deployed, you can learn about its input parameters of the service, that is, the input request type mentioned above, on the **Usage Guides** tab page of the service details page.

The input parameters displayed on the **Usage Guides** tab page depend on the model source that you select.

-  If your model comes from ExeML or a built-in algorithm, the input and output parameters are defined by ModelArts. For details, see the **Usage Guides** tab page. On the **Prediction** tab page, enter the corresponding JSON text or file for service testing.

-  If you use a custom model with the inference code and configuration file compiled by yourself (:ref:`Specifications for Compiling the Model Configuration File <modelarts_23_0092>`), the **Usage Guides** tab page only visualizes your data. The following figure shows the mapping between the input parameters displayed on the **Usage Guides** tab page and the configuration file.

   .. _modelarts_23_0062__en-us_topic_0165025306_fig668522620125:

   .. figure:: /_static/images/en-us_image_0000001156920823.png
      :alt: **Figure 1** Mapping between the configuration file and Usage Guides
   

      **Figure 1** Mapping between the configuration file and Usage Guides

-  If your model is imported using a model template, the input and output parameters vary with the template. For details, see :ref:`Introduction to Model Templates <modelarts_23_0098>`.

.. _modelarts_23_0062__en-us_topic_0165025306_section15840106121611:

JSON Text Prediction
--------------------

#. Log in to the ModelArts management console and choose **Service Deployment** > **Real-Time Services**.
#. On the **Real-Time Services** page, click the name of the target service. The service details page is displayed. On the **Prediction** tab page, enter the prediction code and click **Predict** to perform prediction.

.. _modelarts_23_0062__en-us_topic_0165025306_section1666533761611:

File Prediction (Images and Audios)
-----------------------------------

#. Log in to the ModelArts management console and choose **Service Deployment** > **Real-Time Services**.
#. On the **Real-Time Services** page, click the name of the target service. The service details page is displayed. On the **Prediction** tab page, click **Upload** and select a test file. After the file is uploaded successfully, click **Predict** to perform a prediction test.
