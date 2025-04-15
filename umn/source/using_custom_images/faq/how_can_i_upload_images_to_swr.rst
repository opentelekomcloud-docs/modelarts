:original_name: docker-modelarts_0018.html

.. _docker-modelarts_0018:

How Can I Upload Images to SWR?
===============================

This section describes how to upload images to SWR.

Step 1 Logging In to SWR
------------------------

#. Log in to the SWR console.

#. Click **Create Organization** in the upper right corner and enter an organization name to create an organization. You can customize an organization name. In this case, **deep-learning** is used as an example. The organization name **deep-learning** used in subsequent commands must be replaced with the actual organization name.

#. Click **Generate Login Command** in the upper right corner to obtain a login command.


   .. figure:: /_static/images/en-us_image_0000002268744129.png
      :alt: **Figure 1** Login Command

      **Figure 1** Login Command

#. Log in to the ECS environment as the **root** user and enter the login command.


   .. figure:: /_static/images/en-us_image_0000002233904704.png
      :alt: **Figure 2** Login command executed on the ECS

      **Figure 2** Login command executed on the ECS

Step 2 Uploading Images to SWR
------------------------------

This section describes how to upload an image to SWR.

#. Log in to SWR and tag the image to be uploaded. Replace the organization name **deep-learning** in subsequent commands with the actual organization name configured in step 1.

   .. code-block::

      sudo docker tag tf-1.13.2:latest swr.xxx.com/deep-learning/tf-1.13.2:latest

#. Run the following command to upload the image:

   .. code-block::

      sudo docker push swr.xxx.com/deep-learning/tf-1.13.2:latest


   .. figure:: /_static/images/en-us_image_0000002233744836.png
      :alt: **Figure 3** Uploading an image

      **Figure 3** Uploading an image

#. After the image is uploaded, choose **My Images** on the left navigation pane of the SWR console to view the uploaded custom images.

   **swr.xxx.com/deep-learning/tf-1.13.2:latest** is the SWR URL of the custom image.
