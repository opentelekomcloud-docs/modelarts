:original_name: modelarts_21_0016.html

.. _modelarts_21_0016:

Creating a Project
==================

ModelArts ExeML supports image classification, and object detection projects. You can create any of them based on your needs. Perform the following operations to create an ExeML project.

Procedure
---------

#. Log in to the ModelArts management console. In the left navigation pane, choose **ExeML**. The **ExeML** page is displayed.


   .. figure:: /_static/images/en-us_image_0000002043182284.png
      :alt: **Figure 1** ExeML

      **Figure 1** ExeML

#. Click **Create Project** in the box of your desired project. The page for creating an ExeML project is displayed.

#. Enter a project name and set **Training Data** to the OBS path of the training data. A data file must be specified in the path.

   .. table:: **Table 1** Parameters

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                   |
      +===================================+===============================================================================================================================================================================================================================================================+
      | Name                              | Name of an ExeML project                                                                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                               |
      |                                   | -  Enter a maximum of 20 characters. Only digits, letters, underscores (_), and hyphens (-) are allowed. This parameter is mandatory.                                                                                                                         |
      |                                   | -  The name must start with a letter.                                                                                                                                                                                                                         |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Training Data                     | OBS data path and data file. The selected OBS data path must meet certain specifications. For details, see **Preparing Data > Requirements for Files Uploaded to OBS**.                                                                                       |
      |                                   |                                                                                                                                                                                                                                                               |
      |                                   | -  Only the files and folders described in **Preparing Data > Requirements for Files Uploaded to OBS** can be saved in the training data path. Otherwise, an error will be reported.                                                                          |
      |                                   | -  Do not modify the files in the training data path.                                                                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                                                                               |
      |                                   | .. note::                                                                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                               |
      |                                   |    Only one ExeML project can be created in each OBS bucket path to training data. If you want to create multiple projects with the same dataset, copy the data in the original OBS bucket path to another OBS bucket path, and then create an ExeML project. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Brief description of a project                                                                                                                                                                                                                                |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Create Project**. The system displays a message indicating that the project has been created. Then, the **Label Data** tab page is displayed. You can also view the project whose **Training Status** is **Not Started** on the **ExeML** page. Click the project name to go to the **Label Data** tab page.
