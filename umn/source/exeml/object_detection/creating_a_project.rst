:original_name: modelarts_21_0010.html

.. _modelarts_21_0010:

Creating a Project
==================

ModelArts ExeML supports image classification and object detection projects. You can create any of them based on your needs. Perform the following operations to create an ExeML project.

Procedure
---------

#. Log in to the ModelArts management console. In the left navigation pane, choose **ExeML**. The **ExeML** page is displayed.


   .. figure:: /_static/images/en-us_image_0000002043182448.png
      :alt: **Figure 1** ExeML

      **Figure 1** ExeML

#. Click **Create Project** in the box of your desired project. The page for creating an ExeML project is displayed.

#. On the displayed page, set the parameters by referring to :ref:`Table 1 <en-us_topic_0000002043023968__en-us_topic_0000001799497900_en-us_topic_0284258839_en-us_topic_0169446159_en-us_topic_0169446153_table14961618163816>`.

   .. _en-us_topic_0000002043023968__en-us_topic_0000001799497900_en-us_topic_0284258839_en-us_topic_0169446159_en-us_topic_0169446153_table14961618163816:

   .. table:: **Table 1** Parameters

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                  |
      +===================================+==============================================================================================================================================================================================================================================================================================+
      | Name                              | Name of an ExeML project                                                                                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                              |
      |                                   | -  Enter a maximum of 32 characters. Only digits, letters, underscores (_), and hyphens (-) are allowed. This parameter is mandatory.                                                                                                                                                        |
      |                                   | -  The name must start with a letter.                                                                                                                                                                                                                                                        |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Brief description of a project                                                                                                                                                                                                                                                               |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Dataset Source                    | You can create a dataset or specify an existing dataset.                                                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                              |
      |                                   | -  **Create**: Configure parameters such as **Dataset Name**, **Input Dataset Path**, **Output Dataset Path**, and **Label Set**.                                                                                                                                                            |
      |                                   | -  **Specify**: Select a dataset of the same type from ModelArts Data Management to create an ExeML project. Only datasets of the same type are displayed in the **Dataset Name** drop-down list.                                                                                            |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Dataset Name                      | If you select **Create** for **Dataset Source**, enter a dataset name based on required rules in the text box on the right. If you select **Specify** for **Dataset Source**, select one from available datasets of the same type under the current account displayed in the drop-down list. |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Input Dataset Path                | Select the OBS path to the input dataset. For details about dataset input specifications, see :ref:`Preparing Data <modelarts_21_0003>`.                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                              |
      |                                   | -  Except the files and folders described in **Preparing Data > Requirements for Files Uploaded to OBS**, no other files or folders can be saved in the training data path. Otherwise, an error will be reported.                                                                            |
      |                                   | -  Do not modify the files in the training data path.                                                                                                                                                                                                                                        |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Output Dataset Path               | Select the OBS path for storing the output dataset.                                                                                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                                                                                                              |
      |                                   | .. note::                                                                                                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                                                              |
      |                                   |    The output dataset path cannot be the same as the input dataset path or cannot be the subdirectory of the input dataset path. It is a good practice to select an empty directory in **Output Dataset Path**.                                                                              |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Label Set                         | -  **Label Name**: Enter a label name. The label name can contain only letters, digits, underscores (_), and hyphens (-). which contains 1 to 32 characters.                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                              |
      |                                   | -  **Add Label**: Click **Add Label** to add one or more labels.                                                                                                                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                                                              |
      |                                   | -  Set the label color: You need to set label colors for object detection datasets, but you do not need to set label colors for image classification datasets. Select a color from the color palette on the right of a label, or enter the hexadecimal color code to set the color.          |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Create Project**. The system displays a message indicating that the project has been created. Then, the **Label Data** tab page is displayed. Alternatively, view the created project on the **ExeML** page and click the project name to go to the **Label Data** page.
