:original_name: modelarts_23_0233.html

.. _modelarts_23_0233:

Creating an Algorithm
=====================

Your locally developed algorithms or algorithms developed using other tools can be uploaded to ModelArts for unified management. Note the following when creating a custom algorithm:

#. :ref:`Prerequisites <modelarts_23_0233__en-us_topic_0000001133351332_section13181641194916>`
#. :ref:`Accessing the Algorithm Creation Page <modelarts_23_0233__en-us_topic_0000001133351332_en-us_topic_0000001071986951_section1478003731615>`
#. :ref:`Setting Basic Parameters <modelarts_23_0233__en-us_topic_0000001133351332_en-us_topic_0000001071986951_section1534119614910>`
#. :ref:`Selecting an Algorithm Source <modelarts_23_0233__en-us_topic_0000001133351332_en-us_topic_0000001071986951_section058543274910>`
#. :ref:`Configuring Data Input and Output <modelarts_23_0233__en-us_topic_0000001133351332_section19643153517516>`
#. :ref:`Defining Hyperparameters <modelarts_23_0233__en-us_topic_0000001133351332_en-us_topic_0000001071986951_section1883311313516>`
#. :ref:`Supported Policies <modelarts_23_0233__en-us_topic_0000001133351332_en-us_topic_0000001071986951_section1959512404445>`
#. :ref:`Adding Training Constraints <modelarts_23_0233__en-us_topic_0000001133351332_en-us_topic_0000001071986951_section11326178153512>`
#. :ref:`Follow-up Operations <modelarts_23_0233__en-us_topic_0000001133351332_en-us_topic_0000001071986951_section743865313613>`

.. _modelarts_23_0233__en-us_topic_0000001133351332_section13181641194916:

Prerequisites
-------------

-  Data is available either by creating a dataset in ModelArts or by uploading the dataset used for training to the OBS directory.
-  Your custom script has been uploaded to the OBS directory. For details about how to develop a training script, see :ref:`Developing a Custom Script <modelarts_23_0240_0>`.
-  At least one empty folder has been created in OBS for storing the training output.
-  The OBS directory you use and ModelArts are in the same region.

.. _modelarts_23_0233__en-us_topic_0000001133351332_en-us_topic_0000001071986951_section1478003731615:

Accessing the Algorithm Creation Page
-------------------------------------

#. Log in to the ModelArts management console and click **Algorithm Management** in the left navigation pane.
#. On the **My Algorithms** page, click **Create**. The **Create Algorithm** page is displayed.

.. _modelarts_23_0233__en-us_topic_0000001133351332_en-us_topic_0000001071986951_section1534119614910:

Setting Basic Parameters
------------------------

Basic information includes **Name** and **Description**.


.. figure:: /_static/images/en-us_image_0000001805380534.png
   :alt: **Figure 1** Setting basic parameters

   **Figure 1** Setting basic parameters

.. _modelarts_23_0233__en-us_topic_0000001133351332_en-us_topic_0000001071986951_section058543274910:

Selecting an Algorithm Source
-----------------------------

Select a preset image to create an algorithm.

Set **Image**, **Code Directory**, and **Boot File** based on the algorithm code. Ensure that the framework of the AI engine you select is the same as the one you use for compiling algorithm code. For example, if TensorFlow is used for compiling algorithm code, select TensorFlow when you create an algorithm.

.. table:: **Table 1** Parameters

   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                         | Description                                                                                                                                                                                                                                      |
   +===================================+==================================================================================================================================================================================================================================================+
   | **Preset images**                 | AI engines supported by the new version of training are displayed by default. You can select **Show Old Engines** to select the engines supported by the old version. For details, see :ref:`Introduction to Custom Script <modelarts_23_0283>`. |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Code Directory                    | OBS path for storing the algorithm code. The files required for training, such as the training code, dependency installation packages, and pre-generated models, are uploaded to the code directory.                                             |
   |                                   |                                                                                                                                                                                                                                                  |
   |                                   | The code directory cannot contain irrelevant files or directories. Otherwise, uploading data may fail.                                                                                                                                           |
   |                                   |                                                                                                                                                                                                                                                  |
   |                                   | Do not store training data in the code directory. When the training job starts, the data stored in the code directory will be downloaded to the backend. A large amount of training data may lead to a download failure.                         |
   |                                   |                                                                                                                                                                                                                                                  |
   |                                   | After you create the training job, ModelArts downloads the code directory and its subdirectories to the container.                                                                                                                               |
   |                                   |                                                                                                                                                                                                                                                  |
   |                                   | .. note::                                                                                                                                                                                                                                        |
   |                                   |                                                                                                                                                                                                                                                  |
   |                                   |    -  Any programming language is supported.                                                                                                                                                                                                     |
   |                                   |    -  The number of files (including files and folders) cannot exceed 1,024.                                                                                                                                                                     |
   |                                   |    -  The total file size cannot exceed 5 GB.                                                                                                                                                                                                    |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Boot File                         | The file must be stored in the code directory and end with .py or .pyc. ModelArts supports boot files compiled only in Python.                                                                                                                   |
   |                                   |                                                                                                                                                                                                                                                  |
   |                                   | The boot file in the code directory is used to start a training job.                                                                                                                                                                             |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+


.. figure:: /_static/images/en-us_image_0000001852060437.png
   :alt: **Figure 2** Using a custom script to create an algorithm

   **Figure 2** Using a custom script to create an algorithm

.. _modelarts_23_0233__en-us_topic_0000001133351332_section19643153517516:

Configuring Data Input and Output
---------------------------------

A custom algorithm obtains data from an OBS bucket or dataset for model training. The training output is stored in an OBS bucket. The input and output parameters in your algorithm code must be parsed to enable data exchange between ModelArts and OBS. For details about how to develop code for training on ModelArts, see :ref:`Developing a Custom Script <modelarts_23_0240_0>`.

When creating a custom algorithm, set the input and output parameters defined in the algorithm code.

-  Input path mapping configuration

   .. _modelarts_23_0233__en-us_topic_0000001133351332_table126437359515:

   .. table:: **Table 2** Parameters

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                               |
      +===================================+===========================================================================================================================================================================================================================================+
      | Mapping Name                      | Customizable description of the input parameter, which defaults to **Data Source**                                                                                                                                                        |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Code Path Parameter               | If you use **argparse** in the algorithm code to parse **data_url** into the data input, set the data input parameter to **data_url** when creating the algorithm. Set the name based on the data input parameter in your algorithm code. |
      |                                   |                                                                                                                                                                                                                                           |
      |                                   | The code path parameter must be the same as the data input parameter parsed in your algorithm code. Otherwise, the algorithm code cannot obtain the input data.                                                                           |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Add Constraint                    | Whether data is obtained from a storage path or ModelArts dataset                                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                                                           |
      |                                   | If you select the ModelArts dataset as the data source, the following constraints are added:                                                                                                                                              |
      |                                   |                                                                                                                                                                                                                                           |
      |                                   | -  **Labeling Type**: For details, see :ref:`Creating a Labeling Job <modelarts_23_0010>`.                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                           |
      |                                   | -  **Data Format**, which can be **Default**, **CarbonData**, or both. **Default** indicates the manifest format.                                                                                                                         |
      |                                   |                                                                                                                                                                                                                                           |
      |                                   | -  **Data Segmentation**: available only for image classification, object detection, text classification, and sound classification datasets.                                                                                              |
      |                                   |                                                                                                                                                                                                                                           |
      |                                   |    Possible values are **Segmented dataset**, **Dataset not segmented**, and **Unlimited**. For details, see :ref:`Publishing a Data Version <modelarts_23_0018>`.                                                                        |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Add Input Path Mapping            | Allow multiple data input sources based on the algorithm                                                                                                                                                                                  |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Output path mapping configuration

   .. _modelarts_23_0233__en-us_topic_0000001133351332_table8644335195117:

   .. table:: **Table 3** Parameters

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                    |
      +===================================+================================================================================================================================================================================================================================================+
      | Mapping Name                      | Customizable description of the output parameter, which defaults to **Output Data**                                                                                                                                                            |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Code Path Parameter               | If you use **argparse** in the algorithm code to parse **train_url** into the data output, set the data output parameter to **train_url** when creating the algorithm. Set the name based on the data output parameter in your algorithm code. |
      |                                   |                                                                                                                                                                                                                                                |
      |                                   | The code path parameter must be the same as the data output parameter parsed in your algorithm code. Otherwise, the algorithm code cannot obtain the output path.                                                                              |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Add Output Path Mapping           | Allow multiple data output paths based on the algorithm                                                                                                                                                                                        |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _modelarts_23_0233__en-us_topic_0000001133351332_en-us_topic_0000001071986951_section1883311313516:

Defining Hyperparameters
------------------------

When you use a frequently-used framework to create an algorithm, ModelArts allows you to customize hyperparameters so you can view or modify them anytime. After the hyperparameters are defined, they are displayed in the startup command and transferred to your boot file as CLI parameters.

#. Import hyperparameters.

   You can click **Add hyperparameter** to manually add hyperparameters. Only letters, digits, hyphens (-), underscores (_), commas (,), periods (.), and spaces are allowed.

#. Edit hyperparameters. For details, see :ref:`Table 4 <modelarts_23_0233__en-us_topic_0000001133351332_en-us_topic_0000001071986951_table143901732155115>`.

   .. _modelarts_23_0233__en-us_topic_0000001133351332_en-us_topic_0000001071986951_table143901732155115:

   .. table:: **Table 4** Hyperparameters

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                        |
      +===================================+====================================================================================================================================================================================================================================================================================+
      | Name                              | Hyperparameter name                                                                                                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                                                                    |
      |                                   | Enter 1 to 64 characters. Only letters, digits, hyphens (-), and underscores (_) are allowed.                                                                                                                                                                                      |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Type                              | Type of the hyperparameter, which can be **String**, **Integer**, **Float**, or **Boolean**                                                                                                                                                                                        |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Default                           | Default value of the hyperparameter, which is used for training jobs by default                                                                                                                                                                                                    |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Constraints                       | Click **restrain**. Then, set the value range or enumerates in the displayed dialog box.                                                                                                                                                                                           |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Required                          | Whether the parameter is mandatory. The value can be **Yes** or **No**. If you select **No**, you can delete the hyperparameter on the training job creation page when using this algorithm to create a training job. If you select **Yes**, the hyperparameter cannot be deleted. |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Description of the hyperparameter                                                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                    |
      |                                   | Only letters, digits, spaces, hyphens (-), underscores (_), commas (,), and periods (.) are allowed.                                                                                                                                                                               |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _modelarts_23_0233__en-us_topic_0000001133351332_en-us_topic_0000001071986951_section1959512404445:

Supported Policies
------------------

ModelArts supports auto search. Auto search automatically finds the optimal hyperparameters without any code modification. This improves model precision and convergence speed.

Auto search supports only the following engines:

-  mindspore_1.7.0-cann_5.1.0-py_3.7-euler_2.8.3-aarch64
-  pytorch_1.8.0-cuda_10.2-py_3.7-ubuntu_18.04-x86_64
-  tensorflow_1.15-cann_5.1.0-py_3.7-euler_2.8.3-aarch64
-  tensorflow_2.1.0-cuda_10.1-py_3.7-ubuntu_18.04-x86_64

.. _modelarts_23_0233__en-us_topic_0000001133351332_en-us_topic_0000001071986951_section11326178153512:

Adding Training Constraints
---------------------------

You can add training constraints of the algorithm based on your needs.

-  **Resource Type**: The options are **CPU**, **GPU**, and **Ascend**. You can select multiple options.

-  **Multicard Training**: Select **Supported** or **Not supported**.

-  **Distributed Training**: Select **Supported** or **Not supported**.


   .. figure:: /_static/images/en-us_image_0000001805391738.png
      :alt: **Figure 3** Training constraints

      **Figure 3** Training constraints

Runtime Environment Preview
---------------------------

When creating a training job, click the arrow on |image1| in the lower right corner of the page to know the path of the code directory, boot file, and input and output data in the training container.


.. figure:: /_static/images/en-us_image_0000001852149949.png
   :alt: **Figure 4** Runtime environment preview

   **Figure 4** Runtime environment preview

.. _modelarts_23_0233__en-us_topic_0000001133351332_en-us_topic_0000001071986951_section743865313613:

Follow-up Operations
--------------------

After you submit the request for creating the algorithm, wait until the algorithm is available on the algorithm management page. When the newly created algorithm is available, you can perform other operations.

You can use the algorithm to create a training job and build a model. For details, see :ref:`Creating a Training Job <modelarts_23_0286>`.

.. |image1| image:: /_static/images/en-us_image_0000001805390986.png
