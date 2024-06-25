:original_name: modelarts_06_0004.html

.. _modelarts_06_0004:

How Do I Change the Default Port to Create a Real-Time Service Using a Custom Image?
====================================================================================

A port number (for example, 8443) has been specified in a model configuration file. If you do not specify a port (default port 8080 will be used then) or specify another port during AI application creation, deploying the AI application as a service will fail. In this case, set the port number to 8443 in the AI application to resolve this issue.

To change the default port, do as follows:

#. Log in to the ModelArts management console. In the navigation pane, choose **AI Application Management** > **AI Applications**.
#. Click **Create**. On the page for creating an AI application, set **Meta Model Source** to **Container image** and select a custom image.
#. Configure the container API and port number. Ensure that the port number is the same as that specified in the model configuration file.
#. After the configuration, click **Create now**. Wait until the AI application runs properly.
#. Deploy the AI application as a real-time service again.
