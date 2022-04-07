.. _modelarts_23_0049:

Managing Job Parameters
=======================

You can store the parameter settings in ModelArts during job creation so that you can use the stored settings to create follow-up training jobs, which makes job creation more efficient.

During the operations of creating, editing, and viewing training jobs, the saved job parameter settings are displayed on the **Job Parameter Mgmt** page.

Using a Job Parameter Configuration
-----------------------------------

-  Method 1: Using a job parameter configuration on the **Job Parameter Mgmt** page

   Log in to the ModelArts management console. In the left navigation pane, choose **Training Management** > **Training Jobs**. On the displayed page, click the **Job Parameter Mgmt** tab. In the job parameter list, click **Creating Training Job** for a job parameter configuration to create a training job based on the job parameter configuration.

-  Method 2: Using a job parameter configuration on the **Creating Training Job** page

   On the **Creating Training Job** page, click **One-Click Configuration**. In the displayed dialog box, select the required job parameter configuration to quickly create an available training job.

Editing a Job Parameter Configuration
-------------------------------------

#. Log in to the ModelArts management console. In the left navigation pane, choose **Training Management** > **Training Jobs**. On the displayed page, click the **Job Parameter Mgmt** tab.

#. In the job parameter configuration list, click **Edit** in the **Operation** column in a row.

#. On the displayed page, modify related parameters by referring to "Creating a Training Job" and click **OK** to save the job parameter settings.

   In the existing job parameter settings, the job name cannot be changed.

Deleting a Training Job Parameter Configuration
-----------------------------------------------

#. Log in to the ModelArts management console. In the left navigation pane, choose **Training Management** > **Training Jobs**. On the displayed page, click the **Job Parameter Mgmt** tab.
#. In the job parameter list, click **Delete** in the **Operation** column in a row.
#. In the displayed dialog box, click **OK**.

   .. note::

      Deleted job parameter configurations cannot be recovered. Therefore, exercise caution when performing this operation.
