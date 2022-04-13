.. _modelarts_23_0206:

Importing a Meta Model from a Container Image
=============================================

For AI engines that are not supported by ModelArts, you can import the model you compile to ModelArts from custom images.

Prerequisites
-------------

-  For details about the specifications and description of custom images, see :ref:`Importing a Model Using a Custom Image <modelarts_23_0086>`.
-  The configuration must be provided for a model that you have developed and trained. The file must comply with ModelArts specifications. For details about the specifications, see :ref:`Specifications for Compiling the Model Configuration File <modelarts_23_0092>`. After the compilation is complete, upload the file to the specified OBS directory.
-  The OBS directory you use and ModelArts are in the same region.

Procedure
---------

#. Log in to the ModelArts management console, and choose **Model Management** > **Models** in the left navigation pane. The **Models** page is displayed.
#. Click **Import** in the upper left corner. The **Import** page is displayed.
#. On the **Import** page, set related parameters.

   a. Set basic information about the model. For details about the parameters, see :ref:`Table 1 <modelarts_23_0206__en-us_topic_0207629477_table19428112584211>`.

      .. _modelarts_23_0206__en-us_topic_0207629477_table19428112584211:

      .. table:: **Table 1** Parameters of basic model information

         +-------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter   | Description                                                                                                                                                                         |
         +=============+=====================================================================================================================================================================================+
         | Name        | Model name. The value can contain 1 to 64 visible characters, including Chinese characters. Only letters, Chinese characters, digits, hyphens (-), and underscores (_) are allowed. |
         +-------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Version     | Version of the model to be created. For the first import, the default value is **0.0.1**.                                                                                           |
         +-------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Label       | Model label. A maximum of five model labels are supported.                                                                                                                          |
         +-------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Description | Brief description of the model                                                                                                                                                      |
         +-------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   b. Select the meta model source and set related parameters. **Meta Model Source** has four options based on the scenario. For details, see :ref:`Methods of Importing a Model <modelarts_23_0052__en-us_topic_0171858287_section179419351998>`. Set **Meta Model Source** to **Container image**. For details about the parameters, see :ref:`Table 2 <modelarts_23_0206__en-us_topic_0207629477_table104931647171713>`.

      .. _modelarts_23_0206__en-us_topic_0207629477_table104931647171713:

      .. table:: **Table 2** Parameters of the meta model source

         +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                                     |
         +===================================+=================================================================================================================================================================================================================================================================================================================================================================================================+
         | Container Image Path              | Click |image1| to import the model image from the container image. The model is of the Image type, and you do not need to use **swr_location** in the configuration file to specify the image location.                                                                                                                                                                                         |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                                 |
         |                                   | For details about how to create a custom image, see :ref:`Introduction to Custom Images <modelarts_23_0084>`.                                                                                                                                                                                                                                                                                   |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                                 |
         |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                                                       |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                                 |
         |                                   |    The model image you select will be shared with the administrator, so ensure you have the permission to share the image (images shared with other accounts are unsupported). When you deploy a service, ModelArts deploys the image as an inference service. Ensure that your image can be properly started and provide an inference interface.                                               |
         +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Deployment Type                   | After the model is imported, select the service type that the model is deployed. When deploying a service, you can only deploy the service type selected here. For example, if you only select **Real-time services** here, you can only deploy real-time services after importing the model.                                                                                                   |
         +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Configuration File                | The **Import from OBS** and **Edit online** methods are available. The configuration file must comply with certain specifications in :ref:`Model Package Specifications <modelarts_23_0091>`. If you select **Import from OBS**, you need to specify the OBS path for storing the configuration file. You can enable **View Configuration File** to view or edit the configuration file online. |
         +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter Configuration           | Click |image2| on the right to view the input and output parameters of the model.                                                                                                                                                                                                                                                                                                               |
         +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   c. Set the inference specifications and model description.

      -  **Min. Inference Specs**: If your model requires certain resources to complete inference, you can configure this parameter to set the minimum specifications required for normal inference after the model is deployed as a service. In later versions, the system will allocate resources based on the inference specifications in service deployment. You can also modify the specifications as required during deployment. Note that the specifications configured here are valid only when real-time services are deployed and the dedicated resource pool is used.
      -  **Model Description**: To help other model developers better understand and use your models, provide model descriptions. Click **Add Model Description** and then set the document name and URL. A maximum of three model descriptions are supported.

   d. Check the information and click **Next**. The model is imported.

      In the model list, you can view the imported model and its version. When the model status changes to **Normal**, the model is successfully imported. On this page, you can create new versions, quickly deploy models, publish models to the market, and perform other operations.

Follow-Up Procedure
-------------------

-  **:ref:`Model Deployment <modelarts_23_0058>`**: On the **Models** page, click the triangle next to a model name to view all versions of the model. Locate the row that contains the target version, click **Deploy** in the **Operation** column, and select the deployment type configured when importing the model from the drop-down list. On the **Deploy** page, set parameters by referring to :ref:`Introduction to Model Deployment <modelarts_23_0058>`.

.. |image1| image:: /_static/images/en-us_image_0000001157081003.png

.. |image2| image:: /_static/images/en-us_image_0000001157081001.png

