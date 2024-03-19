:original_name: modelarts_23_0206.html

.. _modelarts_23_0206:

Importing a Meta Model from a Container Image
=============================================

For AI engines that are not supported by ModelArts, you can import the models you compile to ModelArts from custom images.

Prerequisites
-------------

-  For details about the specifications and description of custom images, see .
-  The OBS directory you use and ModelArts are in the same region.

Creating an AI Application
--------------------------

#. Log in to the ModelArts management console, and choose **AI Application Management** > **AI Applications** in the left navigation pane. The **AI Applications** page is displayed.
#. Click **Create** in the upper left corner.
#. On the displayed page, set the parameters.

   a. Set basic information about the AI application. For details about the parameters, see :ref:`Table 1 <modelarts_23_0206__en-us_topic_0207629477_table19428112584211>`.

      .. _modelarts_23_0206__en-us_topic_0207629477_table19428112584211:

      .. table:: **Table 1** Parameters of basic AI application information

         +-------------+-----------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter   | Description                                                                                                                             |
         +=============+=========================================================================================================================================+
         | Name        | Application name. The value can contain 1 to 64 visible characters. Only letters, digits, hyphens (-), and underscores (_) are allowed. |
         +-------------+-----------------------------------------------------------------------------------------------------------------------------------------+
         | Version     | Version of the AI application to be created. For the first import, the default value is **0.0.1**.                                      |
         +-------------+-----------------------------------------------------------------------------------------------------------------------------------------+
         | Label       | AI application label. A maximum of five labels are supported.                                                                           |
         +-------------+-----------------------------------------------------------------------------------------------------------------------------------------+
         | Description | Brief description of an AI application                                                                                                  |
         +-------------+-----------------------------------------------------------------------------------------------------------------------------------------+

   b. Select the meta model source and set related parameters. Set **Meta Model Source** to **Container image**. For details about the parameters, see :ref:`Table 2 <modelarts_23_0206__table3282175014568>`.


      .. figure:: /_static/images/en-us_image_0000001805745252.png
         :alt: **Figure 1** Setting a container image as the meta model source

         **Figure 1** Setting a container image as the meta model source

      .. _modelarts_23_0206__table3282175014568:

      .. table:: **Table 2** Parameters of the meta model source

         +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                                 |
         +===================================+=============================================================================================================================================================================================================================================================================================================================================================================================+
         | Container Image Path              | Click |image1| to import the model image from the container image. The model is of the Image type, and you do not need to use **swr_location** in the configuration file to specify the image location.                                                                                                                                                                                     |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                             |
         |                                   | For details about how to create a custom image, see .                                                                                                                                                                                                                                                                                                                                       |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                             |
         |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                                                   |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                             |
         |                                   |    The model image you select will be shared with the service administrator, so ensure you have the permission to share the image (images shared with other accounts are unsupported). When you deploy a service, ModelArts deploys the image as an inference service. Ensure that your image can be properly started and provide an inference interface.                                   |
         +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Deployment Type                   | After the model is imported, select the service type that the model is deployed. When deploying a service, you can only deploy the service type selected here. For example, if you only select **Real-time services** here, you can only deploy real-time services after importing the model.                                                                                               |
         +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Configuration File                | The **Import from OBS** and **Edit online** methods are available. The configuration file must comply with the specifications in :ref:`Model Package Specifications <modelarts_23_0091>`. If you select **Import from OBS**, you need to specify the OBS path for storing the configuration file. You can enable **View Configuration File** to view or edit the configuration file online. |
         +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter Configuration           | Click |image2| on the right to view the input and output parameters of the model.                                                                                                                                                                                                                                                                                                           |
         +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | AI Application Description        | Provide AI application descriptions to help other AI application developers better understand and use your applications. Click **Add AI Application Description** and set the **Document name** and **URL**. You can add up to three AI application descriptions.                                                                                                                           |
         +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   c. Check the information and click **Next**. The AI application is created.

      In the AI application list, you can view the created AI application and its version. When the status changes to **Normal**, the AI application is successfully created. On this page, you can perform such operations as creating new versions, quickly deploying AI applications, and publishing AI applications.

Follow-Up Procedure
-------------------

:ref:`Deploying the AI Applications as Services <modelarts_23_0058>`: In the AI application list, click the downward arrow on the left of an AI application name to check all versions of the AI application. Locate the row that contains the target version, click **Deploy** in the **Operation** column, and select a deployment type from the drop-down list box. The AI application can be deployed in a deployment type selected during AI application creation.

.. |image1| image:: /_static/images/en-us_image_0000001805757768.png
.. |image2| image:: /_static/images/en-us_image_0000001805917596.png
