:original_name: dataprepare-modelarts-0028.html

.. _dataprepare-modelarts-0028:

Publishing a Data Version
=========================

#. Log in to the ModelArts management console. In the navigation pane on the left, choose **Data Management** > **Datasets**.
#. Locate the row containing the target dataset and click **Publish** in the **Operation** column. Alternatively, click the dataset name to go to the **Dashboard** tab of the dataset, and click **Publish** in the upper right corner.
#. In the displayed dialog box, set the parameters and click **OK**.

   .. table:: **Table 1** Parameters for publishing a dataset

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                      |
      +===================================+==================================================================================================================================================================================================================================================+
      | Version                           | The naming rules of V001 and V002 in ascending order are used by default. A version name can be customized. Only letters, digits, hyphens (-), and underscores (_) are allowed.                                                                  |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Format                            | Only table datasets support version format setting. Available values are **CSV** and **CarbonData**.                                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                  |
      |                                   | .. note::                                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                  |
      |                                   |    If the exported CSV file contains any command starting with =, +, -, or @, ModelArts automatically adds the Tab setting and escapes the double quotation marks (") for security purposes.                                                     |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Splitting                         | Only image classification, object detection, text classification, and sound classification datasets support data splitting.                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                  |
      |                                   | By default, this function is disabled. After this function is enabled, set the training and validation ratios.                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                                                  |
      |                                   | Enter a value ranging from 0 to 1 for **Training Set Ratio**. After the training set ratio is set, the validation set ratio is determined. The sum of the training set ratio and the validation set ratio is 1.                                  |
      |                                   |                                                                                                                                                                                                                                                  |
      |                                   | .. note::                                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                  |
      |                                   |    To ensure the model accuracy, you are advised to set the training set ratio to 0.8 or 0.9.                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                  |
      |                                   | The training set ratio is the ratio of sample data used for model training. The validation set ratio is the ratio of the sample data used for model validation. The training and validation ratios affect the performance of training templates. |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Description of the current dataset version.                                                                                                                                                                                                      |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Hard Example                      | Only image classification and object detection datasets support hard example attributes.                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                                                                  |
      |                                   | By default, this function is disabled. After this function is enabled, information such as the hard example attributes of the dataset are written to the corresponding manifest file.                                                            |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Directory Structure of Dataset Versions
---------------------------------------

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

Take video labeling as an example. After the dataset is published, the labeling result file (XML) is stored in the dataset output directory.

::

   |-- user-specified-output-path
        |-- DatasetName-datasetId
            |-- annotation
                |-- VersionMame1
                    |-- VersionMame1.manifest
                    |-- annotations
                      |-- images
                          |-- videoName1
                             |-- videoName1.timestamp.xml
                           |-- videoName2
                             |-- videoName2.timestamp.xml
               |-- VersionMame2
                   ...
               |-- ...

The key frames for video labeling are stored in the dataset input directory.

.. code-block::

   |-- user-specified-input-path
        |-- images
           |-- videoName1
                |-- videoName1.timestamp.jpg
            |-- videoName2
                |-- videoName2.timestamp.jpg
