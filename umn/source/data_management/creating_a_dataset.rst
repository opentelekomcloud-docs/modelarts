:original_name: modelarts_23_0004.html

.. _modelarts_23_0004:

Creating a Dataset
==================

To manage data using ModelArts, create a dataset. Then you can perform operations on the dataset, such as labeling data, importing data, and publishing the dataset.

Prerequisites
-------------

-  Before using the data management function, you need permissions to access OBS. This function cannot be used if you are not authorized to access OBS. Before using the data management function, go to the **Settings** page and complete access authorization using an agency.
-  You have created OBS buckets and folders for storing data. In addition, the OBS buckets and ModelArts are in the same region.
-  You have uploaded data to be used to OBS.

Procedure
---------

#. Log in to the ModelArts management console. In the left navigation pane, choose **Data Management** > **Datasets**. The **Datasets** page is displayed.
#. Click **Create Dataset**. On the **Create Dataset** page, create datasets of different types based on the data type and data labeling requirements.

   a. Set the basic information, the name and description of the dataset.

      .. _modelarts_23_0004__en-us_topic_0170886809_fig17294143617510:

      .. figure:: /_static/images/en-us_image_0000001157080905.png
         :alt: **Figure 1** Basic information about a dataset


         **Figure 1** Basic information about a dataset

   b. Select a labeling scene and type as required. For details about the types supported by ModelArts, see :ref:`Dataset Types <modelarts_23_0003__en-us_topic_0171496996_section51771731153811>`.

      .. _modelarts_23_0004__en-us_topic_0170886809_fig3599174864:

      .. figure:: /_static/images/en-us_image_0000001110761058.png
         :alt: **Figure 2** Selecting a labeling scene and type


         **Figure 2** Selecting a labeling scene and type

   c. Set the parameters based on the dataset type. For details, see the parameters of the following dataset types:

      -  :ref:`Images (Image Classification, Object Detection, and Image Segmentation) <modelarts_23_0004__en-us_topic_0170886809_section8625131415541>`

   d. Click **Create** in the lower right corner of the page.

      After the dataset is created, the dataset management page is displayed. You can perform the following operations on the dataset: label data, publish dataset versions, manage dataset versions, modify the dataset, import data, and delete the dataset. For details about the operations supported by different types of datasets, see .

.. _modelarts_23_0004__en-us_topic_0170886809_section8625131415541:

Images (Image Classification, Object Detection, and Image Segmentation)
-----------------------------------------------------------------------

.. _modelarts_23_0004__en-us_topic_0170886809_fig773235071210:

.. figure:: /_static/images/en-us_image_0000001157080911.png
   :alt: **Figure 3** Parameters of datasets for image classification and object detection


   **Figure 3** Parameters of datasets for image classification and object detection

.. table:: **Table 1** Dataset parameters

   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                         |
   +===================================+=====================================================================================================================================================================================================================================================================================================================================================================================+
   | Input Dataset Path                | Select the OBS path to the input dataset.                                                                                                                                                                                                                                                                                                                                           |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Output Dataset Path               | Select the OBS path to the output dataset.                                                                                                                                                                                                                                                                                                                                          |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                     |
   |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                                           |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                     |
   |                                   |    The output dataset path cannot be the same as the input dataset path or cannot be the subdirectory of the input dataset path. Select an empty directory as the **Output Dataset Path**.                                                                                                                                                                                          |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Label Set                         | -  **Label Name**: Enter a label name. The label name can contain only letters, digits, underscores (_), and hyphens (-). The name contains 1 to 32 characters.                                                                                                                                                                                                                     |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                     |
   |                                   | -  **Add Label**: Click **Add Label** to add more labels.                                                                                                                                                                                                                                                                                                                           |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                     |
   |                                   | -  Setting a label color: This function is available only for datasets of the object detection type. Select a color from the color palette on the right of a label, or enter the hexadecimal color code to set the color.                                                                                                                                                           |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                     |
   |                                   | -  Setting label attributes: For an object detection dataset, you can click the plus sign (+) on the right to add label attributes after setting a label color. Label attributes are used to distinguish different attributes of the objects with the same label. For example, yellow kittens and black kittens have the same label **cat** and their label attribute is **color**. |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
