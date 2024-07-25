:original_name: datalabel-modelarts_0019.html

.. _datalabel-modelarts_0019:

Creating an Auto Labeling Job
=============================

In addition to manual labeling, ModelArts also provides the auto labeling function to quickly label data, reducing the labeling time by more than 70%. Auto labeling means learning and training are performed based on the labeled images and an existing model is used to quickly label the remaining images.

Context
-------

-  Only labeling jobs of image classification and object detection types support auto labeling.
-  There are at least two types of labels in the labeling job for auto labeling, and each label has been added to at least five images.
-  At least one unlabeled image must exist when you enable auto labeling.
-  Before starting an auto labeling job, ensure that no auto labeling job is in progress.
-  Before starting an auto labeling job, ensure that the image data does not contain any RGBA four-channel images. These images will cause the job to fail. Delete them from the dataset if you find any.

Starting an Auto Labeling Job
-----------------------------

#. Log in to the ModelArts management console. In the navigation pane on the left, choose **Data Management** > **Label Data**. The **Data Labeling** page is displayed.

#. In the labeling job list, locate the target labeling job of the object detection or image classification type, and click **Auto Labeling** in the **Operation** column.

#. On the **Enable Auto Labeling** page, select **Active learning** or **Pre-labeling**. For details, see :ref:`Table 1 <en-us_topic_0000001943986873__en-us_topic_0000001185384429_en-us_topic_0209622045_table898214481813>` and :ref:`Table 2 <en-us_topic_0000001943986873__en-us_topic_0000001185384429_en-us_topic_0209622045_table4748115061313>`.

   .. _en-us_topic_0000001943986873__en-us_topic_0000001185384429_en-us_topic_0209622045_table898214481813:

   .. table:: **Table 1** Active learning

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                              |
      +===================================+==========================================================================================================================================================================================+
      | Auto Labeling Type                | **Active learning**: The system uses semi-supervised learning and hard example filtering to perform auto labeling, reducing manual labeling workload and helping you find hard examples. |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Algorithm Type                    | For a dataset of the image classification type, set the following parameters:                                                                                                            |
      |                                   |                                                                                                                                                                                          |
      |                                   | **Fast**: Use the labeled samples for training.                                                                                                                                          |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Specifications                    | Resource specifications used by an auto labeling job. Only GPU specifications are supported, and the OBT is free of charge.                                                              |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Compute Nodes                     | The default value is **1**, indicating the single-node system mode. Only this parameter value is supported.                                                                              |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0000001943986873__en-us_topic_0000001185384429_en-us_topic_0209622045_table4748115061313:

   .. table:: **Table 2** Pre-labeling

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                           |
      +===================================+=======================================================================================================================================================================================================================================================================================================================================================+
      | Auto Labeling Type                | **Pre-labeling**: Select a model in the **My AI Applications** tab. Ensure that the model type matches the dataset labeling type. After the pre-labeling is complete, if the labeling result complies with the standard labeling format defined by the platform, the system filters hard examples. This step does not affect the pre-labeling result. |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Model and Version                 | -  **My AI Applications**: Select a model as required. Click the drop-down arrow on the left of the target AI application and select a proper version. For details about how to import a model, see :ref:`Creating an AI Application <inference-modelarts-0004>`                                                                                      |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. note::

      -  For labeling jobs of the object detection type, only rectangular boxes can be recognized and labeled when **Active learning** is selected.
      -  If there are too many auto labeling jobs in the system, the jobs may be queued. As a result, the jobs are always in the labeling state. The jobs will run one after another in order.

#. After setting the parameters, click **Submit** to enable auto labeling.

#. In the labeling job list, click a labeling job name to go to the labeling job details page.

#. Click the **To Be Confirmed** tab to view the auto labeling progress.

   You can also enable auto labeling or view the auto labeling history in this tab.

#. After auto labeling is complete, all the labeled images are displayed on the **To Be Confirmed** page.

   -  Image classification labeling job

      On the **To Be Confirmed** page, check whether labels are correct, select the correctly labeled images, and click **OK** to confirm the auto labeling results. The confirmed image will be categorized to the **Labeled** page.

   -  Object detection labeling job

      On the **To Be Confirmed** page, click images to view their labeling details and check whether labels and target bounding boxes are correct. For the correctly labeled images, click **Labeled** to confirm the auto labeling results. The confirmed image will be categorized to the **Labeled** page.
