.. _modelarts_23_0238:

Using Frequently-used Frameworks to Train Models
================================================

If you use frequently-used frameworks, such as TensorFlow and MXNet, to develop algorithms locally, you can select **Frequently-used** to create training jobs and build models.

Prerequisites
-------------

-  Data has been prepared. Specifically, you have created an available dataset in ModelArts, or you have uploaded the dataset used for training to the OBS directory.
-  If you select **Frequently-used** for **Algorithm Source**, prepare the training script and upload it to the OBS directory.
-  At least one empty folder has been created on OBS for storing the training output.
-  The account is not in arrears because resources are consumed when training jobs are running.
-  The OBS directory you use and ModelArts are in the same region.

Precautions
-----------

-  In the dataset directory specified for a training job, the names of the files (such as the image file, audio file, and label file) containing data used for training contain 0 to 255 characters. If the names of certain files in the dataset directory contain over 255 characters, the training job will ignore these files and use data in the valid files for training. If the names of all files in the dataset directory contain over 255 characters, no data is available for the training job and the training job fails.
-  In the training script, the **Data Source** and **Training Output Path** parameters must be set to the OBS path. Use the to perform read and write operations in the path.

.. _modelarts_23_0238__en-us_topic_0216621183_section12188201115920:

Frequently-used AI Frameworks for Training Management
-----------------------------------------------------

ModelArts supports the following AI engines and versions.

.. table:: **Table 1** AI engines supported by training jobs

   +-----------------------+----------------+---------------------+----------------+-----------------------------------+----------------------------------+
   | Environment           | Supported Chip | System Architecture | System Version | AI Engine and Version             | Supported CUDA or Ascend Version |
   +=======================+================+=====================+================+===================================+==================================+
   | TensorFlow            | CPU and GPU    | x86_64              | Ubuntu 16.04   | TF-1.13.1-python3.6               | CUDA 10.0                        |
   +-----------------------+----------------+---------------------+----------------+-----------------------------------+----------------------------------+
   |                       |                |                     |                | TF-2.1.0-python3.6                | CUDA 10.1                        |
   +-----------------------+----------------+---------------------+----------------+-----------------------------------+----------------------------------+
   | Caffe                 | CPU and GPU    | x86_64              | Ubuntu 16.04   | Caffe-1.0.0-python2.7             | CUDA 8.0                         |
   +-----------------------+----------------+---------------------+----------------+-----------------------------------+----------------------------------+
   | Spark_MLlib           | CPU            | x86_64              | Ubuntu 16.04   | Spark-2.3.2-python3.6             | N/A                              |
   +-----------------------+----------------+---------------------+----------------+-----------------------------------+----------------------------------+
   | XGBoost-Sklearn       | CPU            | x86_64              | Ubuntu 16.04   | Scikit_Learn-0.18.1-python3.6     | N/A                              |
   +-----------------------+----------------+---------------------+----------------+-----------------------------------+----------------------------------+
   | PyTorch               | CPU and GPU    | x86_64              | Ubuntu 16.04   | PyTorch-1.3.0-python3.6           | CUDA 10.0                        |
   +-----------------------+----------------+---------------------+----------------+-----------------------------------+----------------------------------+
   |                       |                |                     |                | PyTorch-1.4.0-python3.6           | CUDA 10.1                        |
   +-----------------------+----------------+---------------------+----------------+-----------------------------------+----------------------------------+
   | Ascend-Powered-Engine | Ascend 910     | AArch64             | EulerOS 2.8    | Mindspore-1.1.1-python3.7-aarch64 | C76                              |
   +-----------------------+----------------+---------------------+----------------+-----------------------------------+----------------------------------+
   |                       |                |                     |                | TF-1.15-python3.7-aarch64         | C76                              |
   +-----------------------+----------------+---------------------+----------------+-----------------------------------+----------------------------------+
   | MindSpore-GPU         | CPU and GPU    | x86_64              | Ubuntu 18.04   | MindSpore-1.1.0-python3.7         | CUDA 10.1                        |
   +-----------------------+----------------+---------------------+----------------+-----------------------------------+----------------------------------+

Creating a Training Job
-----------------------

#. Log in to the ModelArts management console. In the left navigation pane, choose **Training Management** > **Training Jobs**. By default, the system switches to the **Training Jobs** page.

#. In the upper left corner of the training job list, click **Create** to switch to the **Create Training Job** page.

#. Set related parameters.

   a. Set the basic information, including **Name**, **Version**, and **Description**. The **Version** information is automatically generated by the system and named in an ascending order of **V001**, **V002**, and so on. You cannot manually modify it.

      Specify **Name** and **Description** according to actual requirements.

   b. Set job parameters, including the data source, algorithm source, and more. For details, see :ref:`Table 2 <modelarts_23_0238__en-us_topic_0216621183_table1819364517144>`.

      .. _modelarts_23_0238__en-us_topic_0216621183_table1819364517144:

      .. table:: **Table 2** Job parameters

         +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter               | Sub-Parameter         | Description                                                                                                                                                                                                                                                                                                          |
         +=========================+=======================+======================================================================================================================================================================================================================================================================================================================+
         | One-Click Configuration | -                     | If you have saved job parameter configurations in ModelArts, click **One-Click Configuration** and select an existing job parameter configuration as prompted to quickly complete parameter setting for the job.                                                                                                     |
         +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Algorithm Source        | Frequently-used       | Select an AI engine and its version and specify **Code Directory** and **Boot File**. The framework selected for the AI engine must be the same as the one you select when compiling training code. For example, if TensorFlow is used in your training code, select TensorFlow when you create a training job.      |
         |                         |                       |                                                                                                                                                                                                                                                                                                                      |
         |                         |                       | For details about the supported AI engines and versions, see :ref:`Frequently-used AI Frameworks for Training Management <modelarts_23_0238__en-us_topic_0216621183_section12188201115920>`.                                                                                                                         |
         |                         |                       |                                                                                                                                                                                                                                                                                                                      |
         |                         |                       | If your model requires Python dependency packages, place the dependency packages and their configuration files in the code directory based on the requirements defined in ModelArts. For details, see :ref:`How Do I Create a Training Job When a Dependency Package Is Referenced in a Model? <modelarts_05_0063>`. |
         +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Data Source             | Dataset               | Select an available dataset and its version from the ModelArts **Data Management** module.                                                                                                                                                                                                                           |
         |                         |                       |                                                                                                                                                                                                                                                                                                                      |
         |                         |                       | -  **Dataset**: Select an existing dataset from the drop-down list. If no dataset is available in ModelArts, no result will be displayed in the drop-down list.                                                                                                                                                      |
         |                         |                       | -  **Version**: Select a version according to the **Dataset** setting.                                                                                                                                                                                                                                               |
         +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         |                         | Data path             | Select the training data from your OBS bucket. On the right of the **Data path** text box, click **Select**. In the dialog box that is displayed, select an OBS folder for storing data.                                                                                                                             |
         +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Training Output Path    | -                     | Select a path for storing the training result.                                                                                                                                                                                                                                                                       |
         |                         |                       |                                                                                                                                                                                                                                                                                                                      |
         |                         |                       | .. note::                                                                                                                                                                                                                                                                                                            |
         |                         |                       |                                                                                                                                                                                                                                                                                                                      |
         |                         |                       |    To minimize errors, select an empty directory for **Training Output Path**. Do not select the directory used for storing the dataset for **Training Output Path**.                                                                                                                                                |
         +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Running Parameter       | -                     | Set the command line parameters in the code based on the algorithm code logic. Make sure that the parameter names are the same as those in the code.                                                                                                                                                                 |
         |                         |                       |                                                                                                                                                                                                                                                                                                                      |
         |                         |                       | For example, **train_steps = 10000**, where **train_steps** is a passing parameter in code.                                                                                                                                                                                                                          |
         +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Job Log Path            | -                     | Select a path for storing log files generated during job running.                                                                                                                                                                                                                                                    |
         +-------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   c. Select resources for the training job.

      .. table:: **Table 3** Resource parameters

         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                                                                                                                                                                                                                              |
         +===================================+==========================================================================================================================================================================================================================================================================================+
         | Resource Pool                     | Select resource pools for the job.                                                                                                                                                                                                                                                       |
         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Type                              | If **Resource Pool** is set to **Public resource pools**, select a resource type. Available resource types are **CPU** and **GPU**.                                                                                                                                                      |
         |                                   |                                                                                                                                                                                                                                                                                          |
         |                                   | The GPU resource delivers better performance, and the CPU resource is more cost effective. If the selected algorithm has been defined to use the CPU or GPU, the resource type is automatically displayed on the page. Select the resource type as required.                             |
         |                                   |                                                                                                                                                                                                                                                                                          |
         |                                   | .. note::                                                                                                                                                                                                                                                                                |
         |                                   |                                                                                                                                                                                                                                                                                          |
         |                                   |    If GPU resources are used in training code, you must select a GPU cluster when selecting a resource pool. Otherwise, the training job may fail.                                                                                                                                       |
         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Specifications                    | Select a resource flavor based on the resource type.                                                                                                                                                                                                                                     |
         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Compute Nodes                     | Set the number of compute nodes. If you set **Compute Nodes** to **1**, the standalone computing mode is used. If you set **Compute Nodes** to a value greater than 1, the distributed computing mode is used. Select a computing mode based on the actual requirements.                 |
         |                                   |                                                                                                                                                                                                                                                                                          |
         |                                   | When **Frequently-used** of **Algorithm Source** is set to **Caffe**, only standalone training is supported, that is, **Compute Nodes** must be set to **1**. For other options of **Frequently-used**, you can select the standalone or distributed mode based on service requirements. |
         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   d. Configure **Notification** and select whether to save the parameters of the training job.

      .. table:: **Table 4** Parameters related to notification and parameter configuration saving

         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                                                                                                                                                                                                                                    |
         +===================================+================================================================================================================================================================================================================================================================================================+
         | Notification                      | Select the resource pool status to be monitored from the event list, and SMN sends a notification message when the event occurs.                                                                                                                                                               |
         |                                   |                                                                                                                                                                                                                                                                                                |
         |                                   | This parameter is optional. You can choose whether to enable subscription based on actual requirements. If you enable subscription, set the following parameters as required:                                                                                                                  |
         |                                   |                                                                                                                                                                                                                                                                                                |
         |                                   | -  **Topic**: indicates the topic name. You can create a topic on the SMN console.                                                                                                                                                                                                             |
         |                                   | -  **Event**: indicates the event to be subscribed to. The options are **OnJobRunning**, **OnJobSucceeded**, and **OnJobFailed**, indicating that training is in progress, successful, and failed, respectively.                                                                               |
         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Saving Training Parameters        | If you select this option, the parameter settings of the current job will be saved to facilitate subsequent job creation.                                                                                                                                                                      |
         |                                   |                                                                                                                                                                                                                                                                                                |
         |                                   | Select **Save Training Parameters** and specify **Configuration Name** and **Description**. After a training job is created, you can switch to the **Job Parameters** tab page to view your saved job parameter settings. For details, see :ref:`Managing Job Parameters <modelarts_23_0049>`. |
         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   e. After setting the parameters, click **Next**.

#. Confirm that the information is correct on the **Confirm** page that is displayed and click **Submit**. Generally, training jobs run for a period of time, which may be several minutes or tens of minutes depending on the amount of your selected data and resources.

   .. note::

      After a training job is created, it is started immediately.

   You can switch to the training job list to view the basic information about training jobs. In the training job list, **Status** of the newly created training job is **Initializing**. If the status changes to **Successful**, the training job ends and the model generated is stored in the location specified by **Training Output Path**. If the status of a training job changes to **Running failed**, click the name of the training job and view the job logs. Troubleshoot the fault based on the logs.
