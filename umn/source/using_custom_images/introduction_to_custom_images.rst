:original_name: modelarts_23_0084.html

.. _modelarts_23_0084:

Introduction to Custom Images
=============================

Frequently-used images are preset in ModelArts. However, if you have special requirements for the deep learning engine or development library, the preset images cannot meet your requirements. To resolve this issue, ModelArts allows image customization so that you can customize runtime engines.

ModelArts runs in containers. Custom images are customized container images running on ModelArts. Custom images support CLI parameters and environment variables in free-text format, featuring high flexibility for various compute engines.

Associated Services
-------------------

Using a custom image may involve the following services:

-  SWR

   Software Repository for Container (SWR) provides easy, secure, and reliable management over container images throughout their lifecycle, facilitating the deployment of containerized applications. You can upload, download, and manage container images through the SWR console, SWR APIs, or community CLI.

   Obtain the custom images used by ModelArts for training or creating models from the SWR service management list. Upload your custom images to SWR.


   .. figure:: /_static/images/en-us_image_0000002340892008.png
      :alt: **Figure 1** Obtaining images

      **Figure 1** Obtaining images

-  OBS

   Object Storage Service (OBS) is a cloud storage service optimized for storing massive amounts of data. It provides unlimited, secure, and highly reliable storage capabilities at a relatively low cost.

   ModelArts exchanges data with OBS. You can store your data in OBS.

-  ECS

   An Elastic Cloud Server (ECS) is a basic computing unit that consists of vCPUs, memory, OS, and Elastic Volume Service (EVS) disks. After an ECS is created, you can use it similarly to how you would use your local PC or physical server.

   You can create a custom image on premises or on an ECS.

Application Scenarios of ModelArts Custom Images
------------------------------------------------

-  **Using a custom image for a training job**

   If you have developed a model or training script locally but the AI engine you used is not supported by ModelArts, create a custom image and upload it to SWR. Then, use this image to create a training job on ModelArts and use the resources provided by ModelArts to train models.

-  **Using a custom image to create a model**

   If you have developed a model using an AI engine that is not supported by ModelArts, to use this model to create a model, do as follows: Create a custom image, import the image to ModelArts, and use it to create a model. The models created in this way can be centrally managed and deployed as services.
