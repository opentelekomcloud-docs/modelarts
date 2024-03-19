:original_name: modelarts_23_0207.html

.. _modelarts_23_0207:

Importing a Meta Model from OBS
===============================

In scenarios where frequently-used frameworks are used for model development and training, you can import the model to ModelArts and use it to create an AI application for unified management.

Prerequisites
-------------

-  The imported model for creating an AI application, inference code, and configuration file must comply with the requirements of ModelArts. For details, see :ref:`Model Package Specifications <modelarts_23_0091>`, :ref:`Specifications for Compiling the Model Configuration File <modelarts_23_0092>`, and :ref:`Specifications for Writing Model Inference Code <modelarts_23_0093>`.
-  The trained model package, inference code, and configuration file have been uploaded to OBS.
-  The OBS directory you use and ModelArts are in the same region.
-  ModelArts of the Arm version does not support model import from OBS.

Creating an AI Application
--------------------------

#. Log in to the ModelArts management console, and choose **AI Application Management** > **AI Applications** in the left navigation pane. The **AI Applications** page is displayed.
#. Click **Create** in the upper left corner.
#. On the displayed page, set the parameters.

   a. Set basic information about the AI application. For details about the parameters, see :ref:`Table 1 <modelarts_23_0207__en-us_topic_0207629478_table19428112584211>`.

      .. _modelarts_23_0207__en-us_topic_0207629478_table19428112584211:

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

   b. Select the meta model source and set related parameters. Set **Meta Model Source** to **OBS**. For details about the parameters, see :ref:`Table 2 <modelarts_23_0207__en-us_topic_0207629478_table1631162916535>`.

      For the meta model imported from OBS, edit the inference code and configuration files by following :ref:`model package specifications <modelarts_23_0091>` and place the inference code and configuration files in the **model** folder storing the meta model. If the selected directory does not comply with the model package specifications, the AI application cannot be created.


      .. figure:: /_static/images/en-us_image_0000001846057601.png
         :alt: **Figure 1** Setting Meta Model Source to OBS

         **Figure 1** Setting Meta Model Source to OBS

      .. _modelarts_23_0207__en-us_topic_0207629478_table1631162916535:

      .. table:: **Table 2** Parameters of the meta model source

         +----------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                  | Description                                                                                                                                                                                                                                                                                   |
         +============================+===============================================================================================================================================================================================================================================================================================+
         | Meta Model                 | Select the model storage path. This path is the training output path specified in the training job.                                                                                                                                                                                           |
         +----------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | AI Engine                  | The corresponding AI engine is automatically associated based on the selected meta model storage path.                                                                                                                                                                                        |
         +----------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Deployment Type            | After the model is imported, select the service type that the model is deployed. When deploying a service, you can only deploy the service type selected here. For example, if you only select **Real-time services** here, you can only deploy real-time services after importing the model. |
         +----------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Configuration File         | By default, the system associates the configuration file stored in OBS. Enable the function to view, edit, or import the model configuration file from OBS.                                                                                                                                   |
         +----------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter Configuration    | Click |image2| on the right to view the input and output parameters of the model.                                                                                                                                                                                                             |
         +----------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Runtime Dependency         | List the dependencies of the selected model on the environment.                                                                                                                                                                                                                               |
         +----------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | AI Application Description | Provide AI application descriptions to help other AI application developers better understand and use your applications. Click **Add AI Application Description** and set the **Document name** and **URL**. You can add up to three AI application descriptions.                             |
         +----------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   c. Check the information and click **Next**. The AI application is created.

      In the AI application list, you can view the created AI application and its version. When the status changes to **Normal**, the AI application is successfully created. On this page, you can perform such operations as creating new versions, quickly deploying AI applications, and publishing AI applications.

Follow-Up Procedure
-------------------

:ref:`Deploying the AI Applications as Services <modelarts_23_0058>`: In the AI application list, click the downward arrow on the left of an AI application name to check all versions of the AI application. Locate the row that contains the target version, click **Deploy** in the **Operation** column, and select a deployment type from the drop-down list box. The AI application can be deployed in a deployment type selected during AI application creation.

.. |image1| image:: /_static/images/en-us_image_0000001805914516.png
.. |image2| image:: /_static/images/en-us_image_0000001805914516.png
