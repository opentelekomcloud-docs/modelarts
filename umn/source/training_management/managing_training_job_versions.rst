:original_name: modelarts_23_0047.html

.. _modelarts_23_0047:

Managing Training Job Versions
==============================

During model building, you may need to frequently tune the data, training parameters, or the model based on the training results to obtain a satisfactory model. ModelArts allows you to manage training job versions to effectively train your model after the tuning. Specifically, ModelArts generates a version each time when a training is performed. You can quickly get the difference between different versions.

Viewing Training Job Versions
-----------------------------

#. Log in to the ModelArts management console. In the left navigation pane, choose **Training Management** > **Training Jobs**. By default, the system switches to the **Training Jobs** page.

#. In the training job list, click the name of a training job.

   By default, the basic information about the latest version is displayed. If there are multiple available versions, click **Select Version** in the upper left corner to view a certain version. Click the downward arrow to the left of the version to display job details.

Comparing Versions of a Training Job
------------------------------------

On the **Version Manager** page, click **View Comparison Result** to view the comparison of all or selected versions of the current training job. The comparison result involves the following information: **Running Parameter**, **F1 Score**, **Recall**, **Precision**, and **Accuracy**.

.. note::

   The **F1 Score**, **Recall**, **Precision**, and **Accuracy** parameters of a training job are displayed only when the job is created using a built-in algorithm. For training jobs created using frequently-used frameworks or custom images, define the output of these parameters in your training script code. These parameters cannot be viewed on the GUI.

Shortcut Operations Based on Training Job Versions
--------------------------------------------------

On the **Version Manager** page, ModelArts provides certain shortcut operation buttons for you to quickly enter the subsequent steps after model training is complete.

.. table:: **Table 1** Shortcut operation button description

   +---------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Shortcut Operation Button | Description                                                                                                                                                                                                                                                                                                                                                                                                                        |
   +===========================+====================================================================================================================================================================================================================================================================================================================================================================================================================================+
   | Create Model              | Creates a model for the current training version. For details about how to create a model, see :ref:`Importing a Model <modelarts_23_0204>`. You can only create models for training jobs in the **Running** status.                                                                                                                                                                                                               |
   +---------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Modify                    | If the training result of the current version does not meet service requirements or the training job fails, click **Modify** to switch to the page where you can modify the job parameter settings. For details about the parameters of the training job, see :ref:`Creating a Training Job <modelarts_23_0046>`. After modifying the job parameter settings as required, click **OK** to start the training job of a new version. |
   +---------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Save Training Parameters  | You can save the job parameter settings of this version as a job parameter configuration, which will be displayed on the **Job Parameter Mgmt** page. Click **More > Save Training Parameters** to switch to the **Training Parameter** page. After confirming that the settings are correct, click **OK**. For details about training parameter management, see :ref:`Managing Job Parameters <modelarts_23_0049>`.               |
   +---------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Stop                      | Click **More > Stop** to stop the training job of the current version. Only training jobs in the **Running** state can be stopped.                                                                                                                                                                                                                                                                                                 |
   +---------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Delete                    | Click **More > Delete** to delete the training job of the current version.                                                                                                                                                                                                                                                                                                                                                         |
   +---------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+


.. figure:: /_static/images/en-us_image_0000001454866205.png
   :alt: **Figure 1** Shortcut operation buttons

   **Figure 1** Shortcut operation buttons
