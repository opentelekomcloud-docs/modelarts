:original_name: inference-modelarts-0005.html

.. _inference-modelarts-0005:

Viewing Details About an AI Application
=======================================

After an AI application is created, you can view its information on the details page.

#. Log in to the ModelArts management console. In the navigation pane on the left, choose **AI Application Management** > **AI Applications**. The **AI Applications** page is displayed.

#. Click the name of the target AI application. The application details page is displayed.

   On the application details page, you can view the basic information and model precision of the AI application, and switch tab pages to view more information.

   .. table:: **Table 1** Basic information about an AI application

      +----------------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | Parameter                  | Description                                                                                                                 |
      +============================+=============================================================================================================================+
      | Name                       | Name of an AI application                                                                                                   |
      +----------------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | Status                     | Status of an AI application                                                                                                 |
      +----------------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | Version                    | Current version of an AI application                                                                                        |
      +----------------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | ID                         | ID of an AI application                                                                                                     |
      +----------------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | Size                       | Size of an AI application                                                                                                   |
      +----------------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | Runtime Environment        | Runtime environment on which the meta model depends                                                                         |
      +----------------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | Meta Model Source          | Path to the meta model                                                                                                      |
      +----------------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | AI Engine                  | AI engine used by an AI application                                                                                         |
      +----------------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | Deployment Type            | Types of the services that an AI application can be deployed                                                                |
      +----------------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | Model Source               | Source of a model, which can be ExeML, built-in algorithm, or custom algorithm                                              |
      +----------------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | Inference Code             | Path to the inference code                                                                                                  |
      +----------------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | Description                | Click the edit button to add the description of an AI application.                                                          |
      +----------------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | AI Application Description | Description document added during the creation of an AI application                                                         |
      +----------------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | Associated Training Job    | Associated training job if the meta model comes from a training job. Click the training job name to go to its details page. |
      +----------------------------+-----------------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 2** Details page of an AI application

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                |
      +===================================+============================================================================================================================================================================================================+
      | Model Precision                   | Model recall, precision, accuracy, and F1 score of an AI application                                                                                                                                       |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter Configuration           | API configuration, input parameters, and output parameters of an AI application                                                                                                                            |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Runtime Dependency                | Model dependency on the environment. If creating a job failed, edit the runtime dependency. After the modification is saved, the system will automatically use the original image to create the job again. |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Events                            | The progress of key operations during AI application creation                                                                                                                                              |
      |                                   |                                                                                                                                                                                                            |
      |                                   | Events are stored for three months and will be automatically cleared then.                                                                                                                                 |
      |                                   |                                                                                                                                                                                                            |
      |                                   | For details about the event types and event information of AI applications, see What "Are the Events and Their Types for an AI Application?" in *FAQs*.                                                    |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Constraint                        | Constraints on deployment, such as the API request mode, deployed system architecture, and supported acceleration card types                                                                               |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Associated Services               | The list of services that an AI application was deployed. Click a service name to go to the service details page.                                                                                          |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
