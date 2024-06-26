:original_name: modelarts_23_0054.html

.. _modelarts_23_0054:

Importing a Meta Model from a Training Job
==========================================

You can create a training job on ModelArts and perform training to obtain a satisfactory model. Then import the model to **Model Management** for centralized management. In addition, you can quickly deploy the model as a service.

Background
----------

-  If a model generated by the ModelArts training job is used, ensure that the training job has been successfully executed and the model has been stored in the corresponding OBS directory. (Data output parameter is **train_url**.)
-  If a model is generated from a training job that uses a frequently-used framework or custom image, upload the inference code and configuration file to the storage directory of the model by referring to :ref:`Model Package Specifications <modelarts_23_0091>`.
-  The OBS directory you use and ModelArts are in the same region.

Creating an AI Application
--------------------------

#. Log in to the ModelArts management console, and choose **AI Application Management** > **AI Applications** in the left navigation pane. The **AI Applications** page is displayed.
#. Click **Create** in the upper left corner.
#. On the displayed page, set the parameters.

   a. Set basic information about the AI application. For details about the parameters, see :ref:`Table 1 <modelarts_23_0054__en-us_topic_0207629475_table19428112584211>`.

      .. _modelarts_23_0054__en-us_topic_0207629475_table19428112584211:

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

   b. Select the meta model source and set related parameters. Set **Meta Model Source** to **Training job**. For details about the parameters, see :ref:`Table 2 <modelarts_23_0054__table84481252115815>`.


      .. figure:: /_static/images/en-us_image_0000001799338648.png
         :alt: **Figure 1** Setting a training job as the meta model source

         **Figure 1** Setting a training job as the meta model source

      .. _modelarts_23_0054__table84481252115815:

      .. table:: **Table 2** Parameters of the meta model source

         +----------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                  | Description                                                                                                                                                                                                                                                                                   |
         +============================+===============================================================================================================================================================================================================================================================================================+
         | Meta Model Source          | Select **Training job**, and select a specified training job that has completed training under the current account and its version from the drop-down lists on the right of **Training Job** and **Version** respectively.                                                                    |
         +----------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Deployment Type            | After the model is imported, select the service type that the model is deployed. When deploying a service, you can only deploy the service type selected here. For example, if you only select **Real-time services** here, you can only deploy real-time services after importing the model. |
         +----------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Inference Code             | Displays the model inference code URL. You can copy this URL directly.                                                                                                                                                                                                                        |
         +----------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter Configuration    | Click |image2| on the right to view the input and output parameters of the model.                                                                                                                                                                                                             |
         +----------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Runtime Dependency         | Dependencies of the selected model on the environment.                                                                                                                                                                                                                                        |
         +----------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | AI Application Description | Provide AI application descriptions to help other AI application developers better understand and use your applications. Click **Add AI Application Description** and set the **Document name** and **URL**. You can add up to three AI application descriptions.                             |
         +----------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   c. Check the information and click **Next**. The AI application is created.

      In the AI application list, you can view the created AI application and its version. When the status changes to **Normal**, the AI application is successfully created. On this page, you can perform such operations as creating new versions, quickly deploying AI applications, and publishing AI applications.

Follow-Up Procedure
-------------------

:ref:`Deploying the AI Applications as Services <modelarts_23_0058>`: In the AI application list, click the downward arrow on the left of an AI application name to check all versions of the AI application. Locate the row that contains the target version, click **Deploy** in the **Operation** column, and select a deployment type from the drop-down list box. The AI application can be deployed in a deployment type selected during AI application creation.

.. |image1| image:: /_static/images/en-us_image_0000001852636501.png
.. |image2| image:: /_static/images/en-us_image_0000001852636501.png
