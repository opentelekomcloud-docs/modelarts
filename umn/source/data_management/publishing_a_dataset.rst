.. _modelarts_23_0018:

Publishing a Dataset
====================

ModelArts distinguishes data of the same source according to versions labeled at different time, which facilitates the selection of dataset versions during subsequent model building and development. After labeling the data, you can publish the dataset to generate a new dataset version.

.. _modelarts_23_0018__en-us_topic_0170886812_section38541340654:

About Dataset Versions
----------------------

-  For a newly created dataset (before publishing), there is no dataset version information. The dataset must be published before being used for model development or training.
-  The default naming rules of dataset versions are V001 and V002 in ascending order. You can customize the version number during publishing.
-  You can set any version to the current directory. Then the details of the version are displayed on the dataset details page.
-  You can obtain the dataset in the manifest file format corresponding to each dataset version based on the value of **Storage Path**. The dataset can be used when you import data or filter hard examples.
-  The version of a table dataset cannot be changed.

.. _publishing-a-dataset-1:

Publishing a Dataset
--------------------

#. Log in to the ModelArts management console. In the left navigation pane, choose **Data Management** > **Datasets**. The **Datasets** page is displayed.

#. In the dataset list, click **Publish** in the **Operation** column.

   Alternatively, you can click the dataset name to go to the **Dashboard** tab page of the dataset, and click **Publish** in the upper right corner.

#. In the displayed dialog box, set the parameters and click **OK**.

   .. table:: **Table 1** Parameters for publishing a dataset

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                      |
      +===================================+==================================================================================================================================================================================================================================================+
      | Version Name                      | The naming rules of V001 and V002 in ascending order are used by default. A version name can be customized. Only letters, digits, hyphens (-), and underscores (_) are allowed.                                                                  |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Format                            | Only table datasets support version format setting. Available values are **CSV** and **CarbonData**.                                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                  |
      |                                   | .. note::                                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                  |
      |                                   |    If the exported CSV file contains any command starting with =, +, -, or @, ModelArts automatically adds the Tab setting and escapes the double quotation marks (") for security purposes.                                                     |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Splitting                         | Only image classification, object detection, text classification, and sound classification datasets support data splitting.                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                  |
      |                                   | By default, this function is disabled. After this function is enabled, you need to set the training and validation ratios.                                                                                                                       |
      |                                   |                                                                                                                                                                                                                                                  |
      |                                   | Enter a value ranging from 0 to 1 for **Training Set Ratio**. After the training set ratio is set, the validation set ratio is determined. The sum of the training set ratio and the validation set ratio is 1.                                  |
      |                                   |                                                                                                                                                                                                                                                  |
      |                                   | The training set ratio is the ratio of sample data used for model training. The validation set ratio is the ratio of the sample data used for model validation. The training and validation ratios affect the performance of training templates. |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Description of the current dataset version.                                                                                                                                                                                                      |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   After the version is published, you can go to the **Version Manager** tab page to view the detailed information. By default, the system sets the latest version to the current directory.

Directory Structure of Related Files After the Dataset Is Published
-------------------------------------------------------------------

Datasets are managed based on OBS directories. After a new version is published, the directory is generated based on the new version in the output dataset path.

Take an image classification dataset as an example. After the dataset is published, the directory structure of related files generated in OBS is as follows:

.. code-block::

   |-- user-specified-output-path
       |-- DatasetName-datasetId
           |-- annotation
               |-- VersionMame1
                   |-- VersionMame1.manifest
               |-- VersionMame2
                   ...
               |-- ...

The following uses object detection as an example. If a manifest file is imported to the dataset, the following provides the directory structure of related files after the dataset is published:

.. code-block::

   |-- user-specified-output-path 
       |-- DatasetName-datasetId 
           |-- annotation 
               |-- VersionMame1 
                   |-- VersionMame1.manifest 
                   |-- annotation
                      |-- file1.xml 
               |-- VersionMame2
                   ...
               |-- ...
