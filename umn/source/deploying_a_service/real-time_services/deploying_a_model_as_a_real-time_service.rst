:original_name: modelarts_23_0060.html

.. _modelarts_23_0060:

Deploying a Model as a Real-Time Service
========================================

After an AI application is prepared, you can deploy the AI application as a real-time service and predict and call the service.

.. note::

   A maximum of 20 real-time services can be deployed by a user.

Prerequisites
-------------

-  Data has been prepared. Specifically, you have created an AI application in the **Normal** state in ModelArts.

Procedure
---------

#. Log in to the ModelArts management console. In the left navigation pane, choose **Service Deployment** > **Real-Time Services**. By default, the system switches to the **Real-Time Services** page.

#. In the real-time service list, click **Deploy** in the upper left corner. The **Deploy** page is displayed.

#. Set parameters for a real-time service.

   a. Set basic information about model deployment. For details about the parameters, see :ref:`Table 1 <modelarts_23_0060__en-us_topic_0165025304_table16373156155613>`.

      .. _modelarts_23_0060__en-us_topic_0165025304_table16373156155613:

      .. table:: **Table 1** Basic parameters of model deployment

         +-------------+----------------------------------------------------------------+
         | Parameter   | Description                                                    |
         +=============+================================================================+
         | Name        | Name of the real-time service. Set this parameter as prompted. |
         +-------------+----------------------------------------------------------------+
         | Description | Brief description of the real-time service.                    |
         +-------------+----------------------------------------------------------------+

   b. Enter key information including the resource pool and AI application configurations. For details, see :ref:`Table 2 <modelarts_23_0060__en-us_topic_0165025304_table10352134481117>`.

      .. _modelarts_23_0060__en-us_topic_0165025304_table10352134481117:

      .. table:: **Table 2** Parameters

         +----------------------------------+----------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                        | Sub-Parameter                                | Description                                                                                                                                                                                                                                                                                         |
         +==================================+==============================================+=====================================================================================================================================================================================================================================================================================================+
         | Resource Pool                    | Public resource pools                        | Instances in the public resource pool can be of the CPU or GPU type.                                                                                                                                                                                                                                |
         +----------------------------------+----------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Resource Pool                    | Dedicated resource pools                     | For details about how to create a dedicated resource pool, see :ref:`Creating a Dedicated Resource Pool <modelarts_23_0076__en-us_topic_0143244658_section4115221610>`. You can select a specification from the resource pool specifications.                                                       |
         +----------------------------------+----------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | AI Application and Configuration | Model Source                                 | Select **My AI Applications**.                                                                                                                                                                                                                                                                      |
         +----------------------------------+----------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         |                                  | AI Application                               | Select the AI application and version that are in the **Normal** state.                                                                                                                                                                                                                             |
         +----------------------------------+----------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         |                                  | Traffic Ratio (%)                            | Set the traffic proportion of the current instance node. Service calling requests are allocated to the current version based on this proportion.                                                                                                                                                    |
         |                                  |                                              |                                                                                                                                                                                                                                                                                                     |
         |                                  |                                              | If you deploy only one version of an AI application, set this parameter to **100%**. If you select multiple versions for gated launch, ensure that the sum of the traffic ratios of multiple versions is **100%**.                                                                                  |
         +----------------------------------+----------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         |                                  | Specifications                               | Select available specifications based on the list displayed on the console. The specifications in gray cannot be used in the current environment.                                                                                                                                                   |
         +----------------------------------+----------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         |                                  | Compute Nodes                                | Set the number of instances for the current AI application version. If you set **Instances** to **1**, the standalone computing mode is used. If you set **Instances** to a value greater than 1, the distributed computing mode is used. Select a computing mode based on the actual requirements. |
         +----------------------------------+----------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         |                                  | Environment Variable                         | Set environment variables and inject them to the pod. To ensure data security, do not enter sensitive information, such as plaintext passwords, in environment variables.                                                                                                                           |
         +----------------------------------+----------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         |                                  | Add AI Application Version and Configuration | If the selected AI application has multiple versions, you can add multiple versions and configure a traffic ratio. You can use grey launch to smoothly upgrade the AI application version.                                                                                                          |
         |                                  |                                              |                                                                                                                                                                                                                                                                                                     |
         |                                  |                                              | .. note::                                                                                                                                                                                                                                                                                           |
         |                                  |                                              |                                                                                                                                                                                                                                                                                                     |
         |                                  |                                              |    Free compute specifications do not support the grey launch of multiple versions.                                                                                                                                                                                                                 |
         +----------------------------------+----------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. After confirming the entered information, complete service deployment as prompted. Generally, service deployment jobs run for a period of time, which may be several minutes or tens of minutes depending on the amount of your selected data and resources.

   .. note::

      After a real-time service is deployed, it is started immediately.

   You can go to the real-time service list to check whether the deployment of the real-time service is complete. In the real-time service list, after the status of the newly deployed service changes from **Deploying** to **Running**, the service is deployed successfully.
