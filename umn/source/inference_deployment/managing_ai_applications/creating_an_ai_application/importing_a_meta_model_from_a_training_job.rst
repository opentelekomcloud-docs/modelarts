:original_name: inference-modelarts-0006.html

.. _inference-modelarts-0006:

Importing a Meta Model from a Training Job
==========================================

You can create a training job in ModelArts to obtain a satisfactory model. Then, you can import the model to **AI Application Management** for centralized management. In addition, you can quickly deploy the model as a service.

Constraints
-----------

-  A model generated from a training job that uses subscribed algorithms can be directly imported to ModelArts without the need to use the inference code or configuration file.
-  ModelArts of the Arm architecture does not support model import from training.

Prerequisites
-------------

-  The training job has been successfully executed, and the model has been stored in the OBS directory where the training output is stored (the input parameter is **train_url**).
-  If a model is generated from a training job that uses a frequently-used framework or custom image, upload the inference code and configuration file to the storage directory of the model by referring to :ref:`Introduction <inference-modelarts-0055>`.
-  The OBS directory you use and ModelArts are in the same region.

Creating an AI Application
--------------------------

#. Log in to the ModelArts management console and choose **AI Application Management** > **AI Applications** in the left navigation pane. The **AI Applications** page is displayed.
#. Click **Create** in the upper left corner.
#. On the displayed page, configure parameters.

   a. Set basic information about the AI application. For details about the parameters, see :ref:`Table 1 <en-us_topic_0000002043183152__en-us_topic_0207629475_table19428112584211>`.

      .. _en-us_topic_0000002043183152__en-us_topic_0207629475_table19428112584211:

      .. table:: **Table 1** Parameters of basic AI application information

         +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                                                                                                                                           |
         +===================================+=======================================================================================================================================================================================================+
         | Name                              | Application name. The value can contain 1 to 64 visible characters. Only letters, digits, hyphens (-), and underscores (_) are allowed.                                                               |
         +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Version                           | Version of the AI application to be created. For the first creation, the default value is **0.0.1**.                                                                                                  |
         |                                   |                                                                                                                                                                                                       |
         |                                   | .. note::                                                                                                                                                                                             |
         |                                   |                                                                                                                                                                                                       |
         |                                   |    After an AI application is created, you can :ref:`create new versions <en-us_topic_0000002043024844__en-us_topic_0171858290_section102881451161111>` using different meta models for optimization. |
         +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Description                       | Brief description of an AI application                                                                                                                                                                |
         +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   b. Select the meta model source and set related parameters. Set **Meta Model Source** to **Training job**. For details about the parameters, see :ref:`Table 2 <en-us_topic_0000002043183152__en-us_topic_0207629475_table104931647171713>`.

      .. _en-us_topic_0000002043183152__en-us_topic_0207629475_table104931647171713:

      .. table:: **Table 2** Parameters of the meta model source

         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                                                                                                                                                                                                                                  |
         +===================================+==============================================================================================================================================================================================================================================================================================+
         | Meta Model Source                 | Select **Training job**.                                                                                                                                                                                                                                                                     |
         |                                   |                                                                                                                                                                                                                                                                                              |
         |                                   | Choose a completed training job under the current account from the **Training Job** drop-down list.                                                                                                                                                                                          |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | AI Engine                         | Inference engine used by the meta model. The engine is automatically matched based on the training job you select.                                                                                                                                                                           |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Inference Code                    | Set inference code for an AI application. The code is used to customize the inference processing logic. Display the inference code URL. You can copy this URL directly.                                                                                                                      |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Runtime Dependency                | List the dependencies of the selected model in the environment.                                                                                                                                                                                                                              |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | AI Application Description        | Provide AI application descriptions to help other AI application developers better understand and use your applications. Click **Add AI Application Description** and set the document name and URL. A maximum of three AI application descriptions are supported.                           |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Deployment Type                   | Select the service types that the application can be deployed. When deploying a service, only the service types selected here are available. For example, if you only select **Real-Time Services** here, you can only deploy the AI application as a real-time service after it is created. |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   c. Confirm the configurations and click **Create now**. The AI application is created.

      In the AI application list, you can view the created AI application and its version. When the status changes to **Normal**, the AI application is successfully created. On this page, you can perform such operations as creating new versions, quickly deploying AI applications, and publishing AI applications.

Follow-Up Procedure
-------------------

:ref:`Deploying an AI Application as a Service <en-us_topic_0000002043024808__section5706068262>`: In the AI application list, click the down arrow on the left of an AI application name to check all versions of the AI application. Locate the row that contains the target version, click **Deploy** in the **Operation** column, and select a deployment type from the drop-down list box. The AI application can be deployed in a deployment type selected during AI application creation.
