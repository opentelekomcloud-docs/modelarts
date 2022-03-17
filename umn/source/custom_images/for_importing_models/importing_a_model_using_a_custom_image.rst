Importing a Model Using a Custom Image
======================================

After creating and uploading a custom image to SWR, you can use the image to import a model and deploy the model as a service on the ModelArts management console.

Prerequisites
-------------

-  You have created a custom image package based on ModelArts specifications. For details about the specifications you need to comply with when using a custom image to import a model, see `Specifications for Custom Images Used for Importing Models <../../custom_images/for_importing_models/specifications_for_custom_images_used_for_importing_models.html>`__.
-  You have uploaded the custom image to SWR. For details, see `Creating and Uploading a Custom Image <../../custom_images/creating_and_uploading_a_custom_image.html#creating-and-uploading-a-custom-image>`__.

Importing a Model
-----------------

Set basic parameters for importing a model according to `Importing a Meta Model from a Container Image <../../model_management/importing_a_model/importing_a_meta_model_from_a_container_image.html>`__. When importing a model using a custom image, pay attention to the settings of **Meta Model Source** and **Configuration File**.

-  **Meta Model Source**

   Select **Container Image**. Click |image1| in the edit box of **Container Image Path** to select an image. The system automatically lists all images uploaded to SWR. Select an image based on the site requirements.

-  **Configuration File**

   The model configuration file needs to be compiled independently. For details about how to compile the model configuration file, see `Specifications for Compiling the Model Configuration File <../../model_package_specifications/specifications_for_compiling_the_model_configuration_file.html>`__. For details about the configuration file examples of a custom image, see `Example of the Custom Image Model Configuration File <../../model_package_specifications/specifications_for_compiling_the_model_configuration_file.html#example-of-the-custom-image-model-configuration-file>`__. After editing the model configuration file based on the ModelArts specifications, upload it to OBS or use **Edit online** on the **Import Model** page.

Deploying a Service
-------------------

After a model is successfully imported using a custom image, that is, the model status is normal, you can deploy the model as a service. On the **Models** page, click **Deploy** in the **Operation** column and select a service type, for example, **Real-time Service**.

You can deploy models as real-time or batch services based on the business logic of your custom image. The procedure for deploying a model imported using other methods is the same as that for deploying a model imported using a custom image. For details, see `Introduction to Model Deployment <../../model_deployment/introduction_to_model_deployment.html>`__.



.. |image1| image:: /_static/images/en-us_image_0000001156920767.png

