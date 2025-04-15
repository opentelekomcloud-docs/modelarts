:original_name: modelarts_06_0004.html

.. _modelarts_06_0004:

How Do I Change the Default Port to Create a Real-Time Service Using a Custom Image?
====================================================================================

A port number (for example, 8443) has been specified in a model configuration file. If you do not specify a port (default port 8080 will be used then) or specify another port during model creation, deploying the model as a service will fail. In this case, set the port number to 8443 in the model to resolve this issue.

To change the default port, do as follows:

#. Log in to the ModelArts management console. In the navigation pane, choose **Model Management (AI Applications)**.
#. Click **Create**. On the page for creating a model, set **Meta Model Source** to **Container image** and select a custom image.
#. Configure the container API and port number. Ensure that the port number is the same as that specified in the model configuration file.
#. After the configuration, click **Create now**. Wait until the model runs properly.
#. Deploy the model as a real-time service again.
