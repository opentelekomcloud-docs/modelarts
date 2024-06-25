:original_name: modelarts_23_0219.html

.. _modelarts_23_0219:

.. _en-us_topic_0000001919187104:

Custom Image Specifications for Creating an AI Application
==========================================================

When creating an image using locally developed models, ensure that they meet the specifications defined by ModelArts.

-  Custom images cannot contain malicious code.

-  A custom image cannot be larger than 30 GB.

-  **External port of images**

   The external service port of the image must be **8080**. The inference interface must be consistent with the URL defined by **apis** in the **config.json** file. The inference interface can be directly accessed when the image is started. The following is an example of accessing the **mnist** image. The image contains the model trained with the **mnist** dataset. The model can identify handwritten digits in images. In this example, *listen_ip* indicates the IP address of the container.

   -  Example request

      .. code-block::

         curl -X POST \ http://{listen_ip}:8080/ \ -F images=@seven.jpg

   -  Sample response

      .. code-block::

         {"mnist_result": 7}

-  **Log file output**

   To ensure that the log content can be displayed normally, the logs must be standard output.

-  **Image boot file**

   To deploy a batch service, set the boot file of an image to **/home/run.sh** and use CMD to set the default boot path. The following is a sample **Dockerfile**.

   **CMD ["sh", "/home/run.sh"]**

-  **Image dependencies**

   To deploy a batch service, install component packages such as Python, JRE/JDK, and ZIP in the image.

-  (Optional) Maintaining HTTP persistent connections for hitless rolling upgrade

   To ensure that services are not interrupted during the rolling upgrade, set **keep-alive** of HTTP to **200**. For example, gunicorn does not support keep-alive by default. You must install gevent and enter **--keep-alive 200 -k gevent** for the boot parameter. The parameter settings vary depending on the service framework. Set the parameters as required.

-  **(Optional) Processing SIGTERM signals and stopping the container**

   To ensure that services are not interrupted during the rolling upgrade, ModelArts must capture SIGTERM signals in the container and wait for 60 seconds after receiving the SIGTERM signals, and then stop the container. If you stop the container in advance, services may be interrupted during the rolling upgrade. To stop the container in advance, ModelArts needs to process all received requests from the time when the SIGTERM signals are received. The processing duration cannot exceed 90 seconds. Example of the **run.sh** script:

   .. code-block::

      #!/bin/bash
      gunicorn_pid=""

      handle_sigterm() {
        echo "Received SIGTERM, send SIGTERM to $gunicorn_pid"
        if [ $gunicorn_pid != "" ]; then
            sleep 60
            kill -15 $gunicorn_pid  #Transfer SIGTERM signals to the gunicorn process.
            wait $gunicorn_pid           #Wait for the gunicorn process to stop completely.
        fi
      }

      trap handle_sigterm TERM
