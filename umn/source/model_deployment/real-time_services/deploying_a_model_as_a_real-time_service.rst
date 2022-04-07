.. _modelarts_23_0060:

Deploying a Model as a Real-Time Service
========================================

After a model is prepared, you can deploy the model as a real-time service and predict and call the service.

.. note::

   A maximum of 20 real-time services can be deployed by a user.

Prerequisites
-------------

-  Data has been prepared. Specifically, you have created a model in the **Normal** state in ModelArts.

Procedure
---------

#. Log in to the ModelArts management console. In the left navigation pane, choose **Service Deployment** > **Real-Time Services**. By default, the system switches to the **Real-Time Services** page.

#. In the real-time service list, click **Deploy** in the upper left corner. The **Deploy** page is displayed.

#. Set parameters for a real-time service.

   a. Set basic information about model deployment. For details about the parameters, see :ref:`Table 1 <modelarts_23_0060__en-us_topic_0165025304_table16373156155613>`.

      .. _modelarts_23_0060__en-us_topic_0165025304_table16373156155613:

      .. table:: **Table 1** Basic parameters of model deployment

         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                                                                                                                                                    |
         +===================================+================================================================================================================================================================================================================+
         | Name                              | Name of the real-time service. Set this parameter as prompted.                                                                                                                                                 |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Auto Stop                         | After this parameter is enabled and the auto stop time is set, a service automatically stops at the specified time. The auto stop function is enabled by default, and the default value is **1 hour later**.   |
         |                                   |                                                                                                                                                                                                                |
         |                                   | The options are **1 hour later**, **2 hours later**, **4 hours later**, **6 hours later**, and **Custom**. If you select **Custom**, you can enter any integer from 1 to 24 hours in the textbox on the right. |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Description                       | Brief description of the real-time service.                                                                                                                                                                    |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   b. Enter key information including the resource pool and model configurations. For details, see :ref:`Table 2 <modelarts_23_0060__en-us_topic_0165025304_table10352134481117>`.

      .. _modelarts_23_0060__en-us_topic_0165025304_table10352134481117:

      .. table:: **Table 2** Parameters

         +-------------------------+-----------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter               | Sub-Parameter               | Description                                                                                                                                                                                                                                                                                |
         +=========================+=============================+============================================================================================================================================================================================================================================================================================+
         | Resource Pool           | Public resource pools       | Instances in the public resource pool can be of the CPU or GPU type.                                                                                                                                                                                                                       |
         +-------------------------+-----------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Resource Pool           | Dedicated resource pools    | For details about how to create a dedicated resource pool, see :ref:`Creating a Dedicated Resource Pool <modelarts_23_0076__en-us_topic_0143244658_section4115221610>`. You can select a specification from the resource pool specifications.                                              |
         +-------------------------+-----------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Model and Configuration | Model Source                | You can select **My Models** or **My Subscriptions** based on site requirements. The models that match the model sources are displayed.                                                                                                                                                    |
         +-------------------------+-----------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         |                         | Model                       | The system automatically associates with the list of available models. Select a model in the **Normal** status and its version.                                                                                                                                                            |
         +-------------------------+-----------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         |                         | Traffic Ratio (%)           | Set the traffic proportion of the current instance node. Service calling requests are allocated to the current version based on this proportion.                                                                                                                                           |
         |                         |                             |                                                                                                                                                                                                                                                                                            |
         |                         |                             | If you deploy only one version of a model, set this parameter to **100%**. If you select multiple versions for gated launch, ensure that the sum of the traffic ratios of multiple versions is **100%**.                                                                                   |
         +-------------------------+-----------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         |                         | Specifications              | If you select **Public resource pools**, you can select the CPU or GPU resources based on site requirements. For details, see :ref:`Table 3 <modelarts_23_0060__en-us_topic_0165025304_table117211414482>`.                                                                                |
         +-------------------------+-----------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         |                         | Compute Nodes               | Set the number of instances for the current model version. If you set **Instances** to **1**, the standalone computing mode is used. If you set **Instances** to a value greater than 1, the distributed computing mode is used. Select a computing mode based on the actual requirements. |
         +-------------------------+-----------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         |                         | Environment Variable        | Set environment variables and inject them to the container instance. To ensure data security, do not enter sensitive information, such as plaintext passwords, in environment variables.                                                                                                   |
         +-------------------------+-----------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         |                         | Add Model and Configuration | ModelArts supports multiple model versions and flexible traffic policies. You can use gated launch to smoothly upgrade the model version.                                                                                                                                                  |
         |                         |                             |                                                                                                                                                                                                                                                                                            |
         |                         |                             | .. note::                                                                                                                                                                                                                                                                                  |
         |                         |                             |                                                                                                                                                                                                                                                                                            |
         |                         |                             |    If the selected model has only one version, the system does not display **Add Model Version and Configuration**.                                                                                                                                                                        |
         +-------------------------+-----------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Traffic Limit           | N/A                         | Maximum number of times a service can be accessed within a second. You can set this parameter as needed.                                                                                                                                                                                   |
         +-------------------------+-----------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

      .. _modelarts_23_0060__en-us_topic_0165025304_table117211414482:

      .. table:: **Table 3** Supported specifications

         +------------------------------------------------+-------------------------------------------------------------------------------------------+
         | Specifications                                 | Description                                                                               |
         +================================================+===========================================================================================+
         | ExeML specifications (CPU)                     | Only be used by models trained in ExeML projects.                                         |
         |                                                |                                                                                           |
         | ExeML specifications (GPU)                     |                                                                                           |
         +------------------------------------------------+-------------------------------------------------------------------------------------------+
         | CPU: 2 vCPUs \| 8 GiB                          | Suitable for models with only CPU loads.                                                  |
         +------------------------------------------------+-------------------------------------------------------------------------------------------+
         | CPU: 8 vCPUs \| 64 GiB GPU: 1 x V100           | Suitable for running GPU models.                                                          |
         +------------------------------------------------+-------------------------------------------------------------------------------------------+
         | CPU: 8 vCPUs \| 32 GiB GPU: 1 x T4             | Suitable for models requiring CPU and GPU (NVIDIA T4) resources.                          |
         +------------------------------------------------+-------------------------------------------------------------------------------------------+
         | Arm: 3 vCPUs \| 6 GiB Ascend: 1 x Ascend 310   | Carrying one Ascend 310 chip, suitable for models requiring Ascend 310 chip resources.    |
         +------------------------------------------------+-------------------------------------------------------------------------------------------+
         | Ascend: 1 x Ascend 910 CPU: 24 vCPUs \| 96 GiB | Carrying one Ascend 910 chip, suitable for models requiring Ascend 910 chip resources.    |
         +------------------------------------------------+-------------------------------------------------------------------------------------------+
         | Ascend: 8 Ascend 910 CPU: 192 vCPUs \| 720 GiB | Carrying eight Ascend 910 chips, suitable for models requiring Ascend 910 chip resources. |
         +------------------------------------------------+-------------------------------------------------------------------------------------------+

#. After confirming the entered information, complete service deployment as prompted. Generally, service deployment jobs run for a period of time, which may be several minutes or tens of minutes depending on the amount of your selected data and resources.

   .. note::

      After a real-time service is deployed, it is started immediately.

   You can go to the real-time service list to view the basic information about the real-time service. In the real-time service list, after the status of the newly deployed service changes from **Deploying** to **Running**, the service is deployed successfully.
