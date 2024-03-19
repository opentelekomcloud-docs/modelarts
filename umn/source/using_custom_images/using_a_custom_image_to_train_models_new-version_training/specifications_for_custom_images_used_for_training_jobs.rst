:original_name: develop-modelarts-0079.html

.. _develop-modelarts-0079:

Specifications for Custom Images Used for Training Jobs
=======================================================

When you use a locally developed model or training script to create a custom image, ensure that the custom image complies with the specifications defined by ModelArts.

Specifications
--------------

-  A custom image cannot be larger than 30 GB. It is best if the custom image is no larger than 15 GB. An oversized image affects the startup of a training job.

-  The **uid** of the default user of a custom image must be **1000**.
-  GPU drivers cannot be installed in an custom image. When you use GPUs to run a training job, ModelArts automatically places the GPU driver in **/usr/local/nvidia** of the training environment.
-  ModelArts does not support the download of open source installation packages. Install the dependencies required by the training job in the custom image.

Creating a Custom Image for Training Jobs
-----------------------------------------

#. Set up the Docker environment on an ECS or a local host.
#. Write a Dockerfile based on your needs and the preceding specifications to build a custom image.
#. Upload the created custom image to SWR.
