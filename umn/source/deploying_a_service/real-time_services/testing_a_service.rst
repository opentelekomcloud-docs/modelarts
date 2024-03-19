:original_name: modelarts_23_0062.html

.. _modelarts_23_0062:

Testing a Service
=================

After an AI application is deployed as a real-time service, you can debug code or add files for testing on the **Prediction** tab page. Based on the input request (JSON text or file) defined by the AI application, the service can be tested in either of the following ways:

#. :ref:`JSON Text Prediction <modelarts_23_0062__en-us_topic_0165025306_section15840106121611>`: If the input type of the AI application of the deployed service is JSON text, that is, the input does not contain files, you can enter the JSON code on the **Prediction** tab page for service testing.
#. :ref:`File Prediction <modelarts_23_0062__en-us_topic_0165025306_section1666533761611>`: If the input type of the AI application of the deployed service is file, including images, audios, and videos, you can add images on the **Prediction** tab page for service testing.

.. note::

   -  If the input type is image, the size of a single image must be less than 8 MB.
   -  The following image types are supported: png, psd, jpg, jpeg, bmp, gif, webp, psd, svg, and tiff.
   -  This function is used for commissioning. In actual production, you are advised to call APIs. You can select :ref:`Accessing a Real-Time Service (Token-based Authentication) <modelarts_23_0063>` based on the authentication mode.

Input Parameters
----------------

For the service that you have deployed, you can learn about its input parameters of the service, that is, the input request type mentioned above, on the **Usage Guides** tab page of the service details page.

The input parameters displayed on the **Usage Guides** tab page depend on the AI application source that you select.

-  If your metamodel comes from ExeML or a built-in algorithm, the input and output parameters are defined by ModelArts. For details, see the **Usage Guides** tab page. On the **Prediction** tab page, enter the corresponding JSON text or file for service testing.

-  If you use a custom metamodel, that is, the inference code and the configuration file are compiled by yourself (:ref:`Specifications for Compiling the Model Configuration File <modelarts_23_0092>`), the **Usage Guides** tab page only visualizes your configuration files. The following figure shows the mapping between the input parameters displayed on the **Usage Guides** tab page and the configuration file.


   .. figure:: /_static/images/en-us_image_0000001799338584.png
      :alt: **Figure 1** Mapping between the configuration file and Usage Guides

      **Figure 1** Mapping between the configuration file and Usage Guides

-  If your metamodel is imported using a model template, the input and output parameters vary with the template. For details, see the description in :ref:`Introduction to Model Templates <modelarts_23_0098>`.

.. _modelarts_23_0062__en-us_topic_0165025306_section15840106121611:

JSON Text Prediction
--------------------

#. Log in to the ModelArts management console and choose **Service Deployment** > **Real-Time Services**.

#. On the **Real-Time Services** page, click the name of the target service. The service details page is displayed. On the **Prediction** tab page, enter the prediction code and click **Predict** to perform prediction.


   .. figure:: /_static/images/en-us_image_0000001846057413.png
      :alt: **Figure 2** Prediction code

      **Figure 2** Prediction code

.. _modelarts_23_0062__en-us_topic_0165025306_section1666533761611:

File Prediction
---------------

#. Log in to the ModelArts management console and choose **Service Deployment** > **Real-Time Services**.

#. On the **Real-Time Services** page, click the name of the target service. The service details page is displayed. On the **Prediction** tab page, click **Upload** and select a test file. After the file is uploaded successfully, click **Predict** to perform a prediction test.


   .. figure:: /_static/images/en-us_image_0000001862682365.png
      :alt: **Figure 3** Image prediction

      **Figure 3** Image prediction
