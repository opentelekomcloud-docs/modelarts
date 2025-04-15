:original_name: inference-modelarts-0020.html

.. _inference-modelarts-0020:

Testing the Deployed Service
============================

After a model is deployed as a real-time service, you can debug code or add files for testing on the **Prediction** tab page. Based on the input request (JSON text or file) defined by the model, the service can be tested in either of the following ways:

#. :ref:`JSON Text Prediction <en-us_topic_0000002268741873__en-us_topic_0165025306_section15840106121611>`: If the input type of the model of the deployed service is JSON text, that is, the input does not contain files, you can enter the JSON code on the **Prediction** tab page for service testing.
#. :ref:`File Prediction <en-us_topic_0000002268741873__en-us_topic_0165025306_section1666533761611>`: If the input type of the model of the deployed service is file, including images, audios, and videos, you can add images on the **Prediction** tab page for service testing.

.. note::

   -  If the input type is image, the size of a single image must be less than 8 MB.
   -  The following image types are supported: png, psd, jpg, jpeg, bmp, gif, webp, psd, svg, and tiff.
   -  This function is used for commissioning. In actual production, you are advised to call APIs. :ref:`Access the real-time service through token-based authentication. <modelarts_23_0063>`

Input Parameters
----------------

For the service that you have deployed, you can learn about its input parameters of the service, that is, the input request type mentioned above, on the **Usage Guides** tab page of the service details page.

The input parameters displayed on the **Usage Guides** tab page depend on the model source that you select.

-  If your metamodel comes from ExeML or a built-in algorithm, the input and output parameters are defined by ModelArts. For details, see the **Usage Guides** tab page. On the **Prediction** tab page, enter the corresponding JSON text or file for service testing.
-  If you use a custom meta model with the inference code and configuration file compiled by yourself (:ref:`Specifications for Writing the Model Configuration File <inference-modelarts-0056>`), the **Usage Guides** tab page only visualizes your data. The following figure shows the mapping between the input parameters displayed on the **Usage Guides** tab page and the configuration file.

.. _en-us_topic_0000002268741873__en-us_topic_0165025306_section15840106121611:

JSON Text Prediction
--------------------

#. Log in to the ModelArts management console and choose **Service Deployment** > **Real-Time Services**.
#. On the **Real-Time Services** page, click the name of the target service. The service details page is displayed. On the **Prediction** tab page, enter the prediction code and click **Predict** to perform prediction.

.. _en-us_topic_0000002268741873__en-us_topic_0165025306_section1666533761611:

File Prediction
---------------

#. Log in to the ModelArts management console and choose **Service Deployment** > **Real-Time Services**.
#. On the **Real-Time Services** page, click the name of the target service. The service details page is displayed. On the **Prediction** tab page, click **Upload** and select a test file. After the file is uploaded successfully, click **Predict** to perform a prediction test.
