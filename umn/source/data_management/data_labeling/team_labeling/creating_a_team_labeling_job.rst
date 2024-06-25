:original_name: datalabel-modelarts_0027.html

.. _datalabel-modelarts_0027:

Creating a Team Labeling Job
============================

If you enable team labeling when creating a labeling job and assign a team to label the dataset, the system creates a labeling job based on the team by default. After creating the labeling job, you can view the job in the **My Creations** tab of the dataset.

You can also create a team labeling job and assign it to different members in the same team or to other labeling teams.

Methods
-------

-  Choose **Data Management** > **Label Data** on the console. When creating a labeling job, enable **Team Labeling** and select a team or task manager.
-  Choose **Data Management** > **Datasets** on the console. In the **Operation** column of the target dataset, click **Labeling**. On the displayed **Create Labeling Job** page, enable **Team Labeling**. You can create multiple team labeling jobs for the same dataset.

   .. note::

      -  Team members receive emails for team labeling jobs. No email will be sent when you create a labeling team or add members to a labeling team. Additionally, after all samples are labeled, no email will be sent when you create a team labeling job.
      -  After a team labeling job is created, all unlabeled samples are assigned to annotators randomly and evenly.

Procedure
---------

You can create multiple team labeling jobs for the same dataset and assign them to different members in the same team or to other labeling teams.

#. Log in to the ModelArts management console. In the navigation pane on the left, choose **Data Management** > **Datasets**.

#. In the dataset list, select a dataset that supports team labeling, and click the dataset name to go to the **Dashboard** tab of the dataset.

#. In the **Labeling Job** area, view existing labeling jobs of the dataset. Click **Create** to create a job.

   Alternatively, you can choose **Data Management** > **Label Data** and click **Create Labeling Job**.

#. In the displayed **Create Labeling Job** page, set parameters and click **Create**.

   -  **Name**: Enter a job name.

   -  **Labeling Scene**: Select the type of the labeling job.

   -  **Label Set**: All existing labels and label attributes of the dataset are displayed.

   -  **Team Labeling**: Click the button on the right and set the following parameters:

      -  **Type**: Select a job type, **Team** or **Task Manager**.
      -  **Select Team**: If **Type** is set to **Team**, select a team and members for labeling. The drop-down list displays the labeling teams and their members created by the current account.
      -  **Select Task Manager**: If **Type** is set to **Task Manager**, select one **Team Manager** member from all teams as the task manager.
      -  **Automatically synchronize new files to the team labeling task**: New files in the dataset will be automatically synchronized to the labeling job that has been started.
      -  **Automatically load the intelligent labeling results to files that need to be labeled**: Files are automatically labeled. Annotators can then accept or modify the labels.

         .. note::

            The process of loading auto labeling results to a team labeling job is as follows:

            -  If you set **Type** to **Team**, you are required to create a team labeling task before executing the job.
            -  If you set **Type** to **Task Manager**, select a team labeling job in the **My Participations** tab and click **Assign Task**.

      After the job is created, you can view the new job in the **My Creations** tab.
