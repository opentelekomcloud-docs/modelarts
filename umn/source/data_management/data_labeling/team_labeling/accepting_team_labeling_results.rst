:original_name: datalabel-modelarts_0031.html

.. _datalabel-modelarts_0031:

Accepting Team Labeling Results
===============================

Task Acceptance (Administrator)
-------------------------------

-  **Initiating acceptance**

   After team members complete data labeling, the labeling job creator can initiate acceptance to check labeling results. The acceptance can be initiated only when a labeling member has labeled data. Otherwise, the acceptance initiation button is unavailable.

   #. Log in to the ModelArts management console. In the navigation pane on the left, choose **Data Management** > **Label Data**.

   #. In the **My Participations** tab, click a team labeling job to go to its details page. Choose **Team Labeling** > **Accept** in the upper right corner.

   #. In the displayed dialog box, set **Sample Policy** to **By percentage** or **By quantity**. Click **OK** to start the acceptance.

      **By percentage**: Sampling is performed based on a percentage for acceptance.

      **By quantity**: Sampling is performed based on quantity for acceptance.

   #. After the acceptance is initiated, an acceptance report is displayed on the console. In the **Acceptance Result** area on the right, click **Pass** or **Reject**.

      If you click **Pass**, set **Rating** to **A**, **B**, **C**, or **D**. Option **A** indicates the highest score. If you click **Reject**, enter your rejection reasons in the text box.

-  **Continuing acceptance**

   You can continue accepting tasks whose acceptance is not completed. For tasks for which an acceptance process is not initiated, the **Continue Acceptance** button is unavailable.

   In the **Labeling Progress** pane in the **Task Statistics** tab, click **Continue Acceptance** to continue accepting jobs. The **Real-Time Acceptance Report** page is displayed. You can continue to accept the images that are not accepted.

-  **Finishing acceptance**

   After the continue acceptance is complete, click **Stop Acceptance** in the upper right corner. On the displayed page, view the acceptance status of the labeling job, such as the number of sampled files, configure parameters, and perform the acceptance. The labeling information is synchronized to the **Labeled** tab of the labeling job only after the acceptance is complete.

   Once the labeled data is accepted, team members cannot modify the labeling information. Only the dataset creator can modify the labeling information.

   .. table:: **Table 1** Parameters for finishing acceptance

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                  |
      +===================================+==============================================================================================================================================================================================================================================+
      | Modifying Labeled Data            | -  **Not overwrite**: For the same data, do not overwrite the existing data with the labeling result of the current team.                                                                                                                    |
      |                                   | -  **Overlays**: For the same data, overwrite the existing data with the labeling result of the current team. Overwritten data cannot be recovered.                                                                                          |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Acceptance Scope                  | -  **All passed**: All items, including the rejected ones will pass the review.                                                                                                                                                              |
      |                                   | -  **All rejects**: All items, including the ones that have passed the review will be rejected. In this case, the passed items must be labeled and reviewed again in the next acceptance.                                                    |
      |                                   | -  **All remaining items pass**: The rejected items are still rejected, and the remaining items will automatically pass the review.                                                                                                          |
      |                                   | -  **All remaining items rejects**: The selected items that have passed the review do not need to be labeled. All the selected items that have been rejected and the items that have not been selected must be labeled again for acceptance. |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Viewing an Acceptance Report
----------------------------

You can view the acceptance report of an ongoing or finished labeling job. Log in to the management console and choose **Data Management** > **Label Data**. On the **Data Labeling** page, select **My Creations** and click the name of a team labeling job. The job details page is displayed. In the upper right corner of the page, click **Acceptance Report**. In the displayed dialog box, view report details.

Deleting a Labeling Job
-----------------------

After a job is accepted, delete it if the labeling job is no longer used. After a job is deleted, the labeling details that are not accepted will be lost. However, the original data in the dataset and the labeled data that has been accepted are still stored in the corresponding OBS bucket.
