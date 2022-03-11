Creating and Uploading a Custom Image
=====================================

ModelArts allows you to use custom images to create training jobs and import models. Before creating and uploading a custom image, understand the following information:

-  Software Repository for Container (SWR)

   SWR provides easy, secure, and reliable management over Docker container images throughout their lifecycle, facilitating the deployment of containerized applications. You can push, pull, and manage container images through SWR console, SWR APIs, or community Command Line Interface (CLI).

   Obtain the custom images used by ModelArts for model training and import from the SWR service management list. Upload the custom images you create to SWR.

-  Specifications for custom images. For details about how to use a custom image for a training job, see `Specifications for Custom Images Used for Training Jobs <../custom_images/for_training_models/specifications_for_custom_images_used_for_training_jobs.html>`__. For details about how to use a custom image for model import, see `Specifications for Custom Images Used for Importing Models <../custom_images/for_importing_models/specifications_for_custom_images_used_for_importing_models.html>`__.

.. _creating-and-uploading-a-custom-image-1:

Creating and Uploading a Custom Image
-------------------------------------

#. Purchase a cloud server or use a local host to set up the Docker environment.
#. Obtain the basic image from the local environment.
#. Compile a Dockerfile based on your requirements to build a custom image. For details about how to efficiently compile a Dockerfile, see *SoftWare Repository for Container Best Practices*.

4. After customizing an image, upload the image to SWR by referring to "Uploading an Image Through a Docker Client" in *Software Repository for Container User Guide*.


