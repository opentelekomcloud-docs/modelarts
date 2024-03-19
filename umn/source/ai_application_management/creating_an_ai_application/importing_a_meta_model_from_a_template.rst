:original_name: modelarts_23_0205.html

.. _modelarts_23_0205:

Importing a Meta Model from a Template
======================================

Because the configurations of models with the same functions are similar, ModelArts integrates the configurations of such models into a common template. By using this template, you can easily and quickly create AI applications without compiling the **config.json** configuration file.

Background
----------

-  Because the configurations of models with the same functions are similar, ModelArts integrates the configurations of such models into a common template. By using this template, you can easily and quickly create AI applications. For details about the template, see :ref:`Introduction to Model Templates <modelarts_23_0098>`.
-  Ensure that you have uploaded the model to OBS according to the model package specifications of the corresponding template.
-  The OBS directory you use and ModelArts are in the same region.

Creating an AI Application
--------------------------

#. Log in to the ModelArts management console, and choose **AI Application Management** > **AI Applications** in the left navigation pane. The **AI Applications** page is displayed.
#. Click **Create** in the upper left corner.
#. On the displayed page, set the parameters.

   a. Set basic information about the AI application. For details about the parameters, see :ref:`Table 1 <modelarts_23_0205__en-us_topic_0207629476_table83985217130>`.

      .. _modelarts_23_0205__en-us_topic_0207629476_table83985217130:

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

   b. Select the meta model source and set related parameters. Set **Meta Model Source** to **Template**. For details about the parameters, see :ref:`Table 2 <modelarts_23_0205__table798114315713>`.


      .. figure:: /_static/images/en-us_image_0000001852501737.png
         :alt: **Figure 1** Setting a template as the meta model source

         **Figure 1** Setting a template as the meta model source

      .. _modelarts_23_0205__table798114315713:

      .. table:: **Table 2** Parameters of the meta model source

         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                      |
         +===================================+==================================================================================================================================================================================================================================================================================================================================================================================================================================================+
         | Model Template                    | Select a template from the existing ModelArts template list .                                                                                                                                                                                                                                                                                                                                                                                    |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
         |                                   | ModelArts also provides three filter criteria: **Type**, **Engine**, and **Environment**, helping you quickly find the desired template. If the three filtering criteria cannot meet your requirements, you can enter keywords to search for the target template.                                                                                                                                                                                |
         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Model Directory                   | OBS path where a model is saved. Select an OBS path for storing the model based on the input requirements of the selected model template.                                                                                                                                                                                                                                                                                                        |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
         |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                                                                                                        |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
         |                                   |    If a training job is executed for multiple times, different version directories are generated, such as V001 and V002, and the generated models are stored in the **model** folder in different version directories. When selecting model files, specify the **model** folder in the corresponding version directory.                                                                                                                          |
         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Input and Output Mode             | If the default input and output mode of the selected template can be overwritten, you can select an input and output mode based on the AI application function or application scenario. **Input and Output Mode** is an abstract of the API (**apis**) in **config.json**. It describes the interface provided by the AI application for external inference. An input and output mode describes one or more APIs, and corresponds to a template. |
         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | **Deployment Type**               | After the model is imported, select the service type that the model is deployed. When deploying a service, you can only deploy the service type selected here. For example, if you only select **Real-time services** here, you can only deploy real-time services after importing the model.                                                                                                                                                    |
         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | AI Application Description        | Provide AI application descriptions to help other AI application developers better understand and use your applications. Click **Add AI Application Description** and set the **Document name** and **URL**. You can add up to three AI application descriptions.                                                                                                                                                                                |
         +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   c. Check the information and click **Next**. The AI application is created.

      In the AI application list, you can view the created AI application and its version. When the status changes to **Normal**, the AI application is successfully created. On this page, you can perform such operations as creating new versions, quickly deploying AI applications, and publishing AI applications.

Follow-Up Procedure
-------------------

:ref:`Deploying the AI Applications as Services <modelarts_23_0058>`: In the AI application list, click the downward arrow on the left of an AI application name to check all versions of the AI application. Locate the row that contains the target version, click **Deploy** in the **Operation** column, and select a deployment type from the drop-down list box. The AI application can be deployed in a deployment type selected during AI application creation.
