.. _modelarts_23_0210:

Managing Team Labeling Tasks
============================

For datasets with team labeling enabled, you can create team labeling tasks and assign the labeling tasks to different teams so that team members can complete the labeling tasks together. During data labeling, members can initiate acceptance, continue acceptance, and view acceptance reports.

.. _modelarts_23_0210__en-us_topic_0209053802_section72262410214:

Creating Team Labeling Tasks
----------------------------

If you enable team labeling when creating a dataset and assign a team to label the dataset, the system creates a labeling task based on the team by default. After the dataset is created, you can view the labeling task on the **Labeling Progress** tab page of the dataset.

You can also create a team marking task and assign it to different members in the same team or to other labeling teams.

#. Log in to the ModelArts management console. In the left navigation pane, choose **Data Management** > **Datasets**. A dataset list is displayed.
#. In the dataset list, select a dataset that supports team labeling, and click the dataset name to go to the **Dashboard** tab page of the dataset.
#. Click the **Labeling Progress** tab to view existing labeling tasks of the dataset. Click **Create Team Labeling Task** in the upper right corner to create a task.
#. In the displayed **Create Team Labeling Task** dialog box, set related parameters and click **OK**.

   -  **Name**: Enter a task name.

   -  **Type**: Select a task type, **Team** or **Task Manager**.

   -  **Select Team**: If **Type** is set to **Team**, you need to select a team and members for labeling. The **Select Team** drop-down list lists the labeling teams and members created by the current account. For details about team management, see :ref:`Introduction to Team Labeling <modelarts_23_0181>`.

   -  **Select Task Manager**: If **Type** is set to **Task Manager**, you need to select one **Team Manager** member from all teams as the task manager.

   -  **Label Set**: All existing labels and label attributes of the dataset are displayed. You can also select **Automatically synchronize new images to the team labeling task** or **Automatically load the intelligent labeling results to images that need to be labeled** under **Label Set**.

      The process of loading auto labeling results to a team labeling task is as follows:

      -  If you set **Type** to **Team**, you are required to create a team labeling task before executing the task.
      -  If you set **Type** to **Task Manager**, you are required to log in to the data labeling console and assign a labeling task before executing the task.

      After the task is created, you can view the new task on the **Labeling Progress** tab page.

Labeling (Team Member)
----------------------

After a labeling task is created, the team member to which the task is assigned receives a labeling notification email.

In the email details, click the labeling task link and use your email address and initial password to log in to the labeling platform. After login, change the password. After logging in to the labeling platform, you can view the assigned labeling task and click the task name to go to the labeling page. The labeling method varies depending on the dataset type. For details, see the following:

-  :ref:`Image Classification <modelarts_23_0011__en-us_topic_0170889731_section888019266174>`
-  :ref:`Object Detection <modelarts_23_0012__en-us_topic_0170889732_section888019266174>`
-  :ref:`Text Classification <modelarts_23_0013__en-us_topic_0170889733_section888019266174>`
-  :ref:`Named Entity Recognition <modelarts_23_0014__en-us_topic_0170889734_section888019266174>`
-  :ref:`Text Triplet <modelarts_23_0211__en-us_topic_0209128667_section888019266174>`

On the labeling platform, each member can view the images that are not labeled, to be corrected, rejected, to be reviewed, approved, and accepted. Pay attention to the images rejected by the administrator and the images to be corrected.

If the Reviewer role is assigned for a team labeling task, the labeling result needs to be reviewed. After the labeling result is reviewed, it is submitted to the administrator for acceptance.

.. _modelarts_23_0210__en-us_topic_0209053802_fig13465256141515:

.. figure:: /_static/images/en-us_image_0000001110760934.png
   :alt: **Figure 1** Labeling platform


   **Figure 1** Labeling platform

Task Acceptance (Administrator)
-------------------------------

-  **Initiating acceptance**

   After team members complete data labeling, the dataset creator can initiate acceptance to check labeling results. The acceptance can be initiated only when a labeling member has labeled data. Otherwise, the acceptance initiation button is unavailable.

   #. On the **Labeling Progress** tab page, click **Initiate Acceptance** to accept tasks.

   #. In the displayed dialog box, set **Sample Policy** to **By percentage** or **By quantity**. Click **OK** to start the acceptance.

      **By percentage**: Sampling is performed based on a percentage for acceptance.

      **By quantity**: Sampling is performed based on quantity for acceptance.

   #. After the acceptance is initiated, an acceptance report is displayed on the console in real time. In the **Acceptance Result** area on the right, select **Pass** or **Reject**.

      If you select **Pass**, set **Rating** to **A**, **B**, **C**, or **D**. Option **A** indicates the highest score. If you select **Reject**, enter your rejection reasons in the text box.

-  **Continuing acceptance**

   You can continue accepting tasks whose acceptance is not completed. For tasks for which an acceptance process is not initiated, the **Continue Acceptance** button is unavailable.

   On the **Labeling Progress** tab page, click **Continue Acceptance** to continue accepting tasks. The **Real-Time Acceptance Report** page is displayed. You can continue to accept the images that are not accepted.

-  **Finishing acceptance**

   In the acceptance completion window, you can view dataset acceptance details, such as the number of sample files, set the following parameters, and perform acceptance. The labeling information is synchronized to the **Labeled** tab page of the dataset only after the acceptance is complete.

   Once the labeled data is accepted, team members cannot modify the labeling information. Only the dataset creator can modify the labeling information.

   .. table:: **Table 1** Parameters for finishing acceptance

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                         |
      +===================================+=====================================================================================================================================================================================================================+
      | Modifying Labeled Data            | -  **Not overwrite**: For the same data, do not overwrite the existing data with the labeling result of the current team.                                                                                           |
      |                                   | -  **Overlays**: For the same data, overwrite the existing data with the labeling result of the current team. Overwritten data cannot be recovered. Exercise caution when performing this operation.                |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Acceptance Scope                  | -  All: all data that has been labeled by the current team, including **Accepted**, **Pending Acceptance**, and **Rejected** data. It refers to all sample files in the dataset.                                    |
      |                                   |                                                                                                                                                                                                                     |
      |                                   | -  All rejects: rejects all data that has been labeled by the current team. That is, all labeled data is rejected to the labeling personnel.                                                                        |
      |                                   |                                                                                                                                                                                                                     |
      |                                   | -  Accepted and pending acceptance: accepts the data that passes the acceptance or is in the Pending Acceptance state in the sample files and rejects the data that fails the acceptance to the labeling personnel. |
      |                                   |                                                                                                                                                                                                                     |
      |                                   | -  Accepted: accepts the data that has passed the acceptance in the sample files and rejects the data that is in the Pending Acceptance state or fails the acceptance to the labeling personnel.                    |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Viewing an Acceptance Report
----------------------------

You can view the acceptance report of an ongoing or finished labeling task. On the **Labeling Progress** tab page, click **Acceptance Report**. In the displayed **Acceptance Report** dialog box, view report details.

Deleting a Labeling Task
------------------------

On the **Labeling Progress** tab page, click **Delete** in the row where a labeling task to be deleted. After a task is deleted, the labeling details that are not accepted will be lost. Exercise caution when performing this operation. However, the original data in the dataset and the labeled data that has been accepted are still stored in the corresponding OBS bucket.
