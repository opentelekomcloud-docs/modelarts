.. _modelarts_23_0219:

Specifications for Custom Images Used for Importing Models
==========================================================

When creating an image using locally developed models, ensure that they meet the specifications defined by ModelArts.

Specifications for Custom Images Used for Model Management
----------------------------------------------------------

-  Custom images cannot contain malicious code.

-  The size of a custom image cannot exceed 30 GB.

-  **External port of images**

   The external service port of the image must be **8080**. The inference interface must be consistent with the URL defined by **apis** in the **config.json** file. The inference interface can be directly accessed when the image is started. The following is an example of accessing the **mnist** image. The image contains the model trained with the **mnist** dataset. The model can identify handwritten digits in images. In this example, *listen_ip* indicates the IP address of the container.

   -  Sample request: **curl -X POST \\ http://{listen_ip}:8080/ \\ -F images=@seven.jpg**

   -  Sample response

      .. code-block::

         {"mnist_result": 7}

-  **Health check port**

   A custom image must provide a health check interface for ModelArts to call. The health check interface is configured in the **config.json** file. For details, see the model configuration file compilation description. A sample health check interface is as follows:

   -  URI

      .. code-block::

         GET /health

   -  Sample request: **curl -X GET \\ http://{listen_ip}:8080/health**

   -  Sample response

      .. code-block::

         {"health": "true"}

   -  Status code

      .. table:: **Table 1** Status code

         =========== ======= ==================
         Status Code Message Description
         =========== ======= ==================
         200         OK      Successful request
         =========== ======= ==================

-  **Log file output**

   To ensure that the log content can be displayed normally, the logs must be standard output.

-  **Image boot file**

   To deploy a batch service, set the boot file of an image to **/home/run.sh** and use CMD to set the default boot path. The following is a sample **Dockerfile**.

   **CMD /bin/sh /home/run.sh**

-  **Image dependencies**

   To deploy a batch service, install component packages such as Python, JRE/JDK, and ZIP in the image.
