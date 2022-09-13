:original_name: modelarts_21_0016.html

.. _modelarts_21_0016:

Creating a Project
==================

ModelArts ExeML supports image classification, object detection, and predictive analytics projects. You can create any of them based on your needs. Perform the following operations to create an ExeML project.

Procedure
---------

#. Log in to the ModelArts management console. In the left navigation pane, click **ExeML**. The **ExeML** page is displayed.
#. Click **Create Project** in the box of your desired project. The page for creating an ExeML project is displayed.
#. Enter a project name and set **Training Data** to the OBS path of the training data. A data file must be specified in the path.

   .. table:: **Table 1** Parameter description

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                   |
      +===================================+===============================================================================================================================================================================================================================================================+
      | Name                              | Name of an ExeML project                                                                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                               |
      |                                   | -  Enter a maximum of 32 characters. Only digits, letters, underscores (_), and hyphens (-) are allowed. This parameter is mandatory.                                                                                                                         |
      |                                   | -  The name must start with a letter.                                                                                                                                                                                                                         |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Training Data                     | OBS data path and data file. The selected OBS data path must meet certain specifications. For details, see **Preparing Data > Requirements for Files Uploaded to OBS**.                                                                                       |
      |                                   |                                                                                                                                                                                                                                                               |
      |                                   | -  Except the files and folders described in **Preparing Data > Requirements for Files Uploaded to OBS**, no other files or folders can be saved in the training data path. Otherwise, an error will be reported.                                             |
      |                                   | -  Do not modify the files in the training data path.                                                                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                                                                               |
      |                                   | .. note::                                                                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                               |
      |                                   |    Only one ExeML project can be created in each OBS bucket path to training data. If you want to create multiple projects with the same dataset, copy the data in the original OBS bucket path to another OBS bucket path, and then create an ExeML project. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Brief description of a project                                                                                                                                                                                                                                |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Create Project**. The system displays a message indicating that the project is created successfully. Then, the **Label Data** tab page is displayed. You can also view the project on the **ExeML** page. Click the project name to go to the **Label Data** tab page.
