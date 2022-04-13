.. _modelarts_23_0205:

Importing a Meta Model from a Template
======================================

Because the configurations of models with the same functions are similar, ModelArts integrates the configurations of such models into a common template. By using this template, you can easily and quickly import models without compiling the **config.json** configuration file.

Background
----------

-  Because the configurations of models with the same functions are similar, ModelArts integrates the configurations of such models into a common template. By using this template, you can easily and quickly import the model. For details about the template, see :ref:`Introduction to Model Templates <modelarts_23_0098>`.
-  For details about the supported templates, see :ref:`Supported Templates <modelarts_23_0098__en-us_topic_0172873520_section44801025155417>`. For details about the input and output modes of each template, see :ref:`Supported Input and Output Modes <modelarts_23_0098__en-us_topic_0172873520_section737759781>`.
-  Ensure that you have uploaded the model to OBS based on the model package specifications of the corresponding template.
-  The OBS directory you use and ModelArts are in the same region.

Procedure
---------

#. Log in to the ModelArts management console, and choose **Model Management** > **Models** in the left navigation pane. The **Models** page is displayed.
#. Click **Import** in the upper left corner. The **Import** page is displayed.
#. On the **Import** page, set related parameters.

   a. Set basic information about the model. For details about the parameters, see :ref:`Table 1 <modelarts_23_0205__en-us_topic_0207629476_table83985217130>`.

      .. _modelarts_23_0205__en-us_topic_0207629476_table83985217130:

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

   b. Select the meta model source and set related parameters. Set **Meta Model Source** based on your application scenario. For details, see :ref:`Methods of Importing a Model <modelarts_23_0052__en-us_topic_0171858287_section179419351998>`.If **Meta Model Source** is set to **Template**, set other parameters by referring to :ref:`Table 2 <modelarts_23_0205__en-us_topic_0207629476_table104931647171713>`.

      .. _modelarts_23_0205__en-us_topic_0207629476_table104931647171713:

      .. table:: **Table 2** Parameters of the meta model source

         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                                                                    |
         +===================================+================================================================================================================================================================================================================================================================================================================================================================================================================================+
         | Model Template                    | Select a template from the existing ModelArts template list .                                                                                                                                                                                                                                                                                                                                                                  |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                |
         |                                   | ModelArts also provides three filter criteria: **Type**, **Engine**, and **Environment**, helping you quickly find the desired template. If the three filter criteria cannot meet your requirements, you can enter keywords to search for the target template. For details about the supported templates, see :ref:`Supported Templates <modelarts_23_0098__en-us_topic_0172873520_section44801025155417>`.                    |
         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Model Directory                   | OBS path where a model is saved. Select an OBS path for storing the model based on the input requirements of the selected model template.                                                                                                                                                                                                                                                                                      |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                |
         |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                                                                                      |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                |
         |                                   |    If a training job is executed for multiple times, different version directories are generated, such as V001 and V002, and the generated models are stored in the **model** folder in different version directories. When selecting model files, specify the **model** folder in the corresponding version directory.                                                                                                        |
         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Input and Output Mode             | If the default input and output mode of the selected template can be overwritten, you can select an input and output mode based on the model function or application scenario. **Input and Output Mode** is an abstract of the API (**apis**) in **config.json**. It describes the interface provided by the model for external inference. An input and output mode describes one or more APIs, and corresponds to a template. |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                |
         |                                   | For details about the supported input and output modes, see :ref:`Supported Input and Output Modes <modelarts_23_0098__en-us_topic_0172873520_section737759781>`.                                                                                                                                                                                                                                                              |
         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Deployment Type                   | After the model is imported, select the service type that the model is deployed. When deploying a service, you can only deploy the service type selected here. For example, if you only select **Real-time services** here, you can only deploy real-time services after importing the model.                                                                                                                                  |
         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   c. Set the inference specifications and model description.

      -  **Min. Inference Specs**: If your model requires certain resources to complete inference, you can configure this parameter to set the minimum specifications required for normal inference after the model is deployed as a service. In later versions, the system will allocate resources based on the inference specifications in service deployment. You can also modify the specifications as required during deployment. Note that the specifications configured here are valid only when real-time services are deployed and the dedicated resource pool is used.
      -  **Model Description**: To help other model developers better understand and use your models, provide model descriptions. Click **Add Model Description** and then set the document name and URL. A maximum of three model descriptions are supported.

   d. Check the information and click **Next**. The model is imported.

      In the model list, you can view the imported model and its version. When the model status changes to **Normal**, the model is successfully imported. On this page, you can create new versions, quickly deploy models, publish models to the market, and perform other operations.

Follow-Up Procedure
-------------------

-  **:ref:`Model Deployment <modelarts_23_0058>`**: On the **Models** page, click the triangle next to a model name to view all versions of the model. Locate the row that contains the target version, click **Deploy** in the **Operation** column, and select the deployment type configured when importing the model from the drop-down list. On the **Deploy** page, set parameters by referring to :ref:`Introduction to Model Deployment <modelarts_23_0058>`.
