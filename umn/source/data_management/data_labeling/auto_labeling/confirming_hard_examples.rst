:original_name: datalabel-modelarts_0020.html

.. _datalabel-modelarts_0020:

Confirming Hard Examples
========================

In a labeling task that processes a large amount of data, auto labeling results cannot be directly used for training because the labeled images are insufficient at the initial stage of labeling. It takes a lot of time and manpower to adjust and confirm all unlabeled data one by one. To accelerate labeling progress, ModelArts embeds an auto hard example detection function for labeling unlabeled data in an auto labeling task. This function provides suggestions on labeling priorities for remaining unlabeled images. The auto labeling result of an image with high labeling priority is not as expected. Therefore, this case is called a hard example.

The auto hard example detection function is used to automatically label hard examples during auto labeling and data collection and filtering. Further confirm and label hard example data, and add labeling results to the training dataset to obtain a trained model with higher precision. No manual intervention is required for hard example detection, and you only need to confirm and modify the labeled data, improving data management and labeling efficiency. In addition, you can supplement data similar to hard examples to improve the variety of the dataset and further improve the model training precision.

Hard example management involves three scenarios.

-  :ref:`Confirming Hard Examples After Auto Labeling <en-us_topic_0000002340893858__en-us_topic_0000001185265241_en-us_topic_0217235047_section12530766412>`
-  :ref:`Labeling Data in a Dataset as Hard Examples <en-us_topic_0000002340893858__en-us_topic_0000001185265241_en-us_topic_0217235047_section176081753173911>`

.. note::

   Only datasets of image classification and object detection types support the auto hard example detection function.

.. _en-us_topic_0000002340893858__en-us_topic_0000001185265241_en-us_topic_0217235047_section12530766412:

Confirming Hard Examples After Auto Labeling
--------------------------------------------

During the execution of an auto labeling task, ModelArts automatically detects and labels hard examples. After the auto labeling task is complete, the labeling results of hard examples are displayed in the **To Be Confirmed** tab. Modify hard example data and confirm the labeling result.

#. Log in to the ModelArts management console. In the navigation pane, choose **Data Management** > **Label Data**. On the **Data Labeling** page, click **My Creations**.
#. In the labeling job list, select a labeling job of the object detection or image classification type and click the labeling job name to go to the labeling job details page.
#. In the **Labeling** tab, click **To Be Confirmed** to check and confirm hard examples.

   .. note::

      Labeling data is displayed in the **To Be Confirmed** tab only after the auto labeling task is complete. Otherwise, no data is available in the tab. For details about auto labeling, see :ref:`Creating an Auto Labeling Job <datalabel-modelarts_0019>`.

   -  For labeling jobs of the object detection type

      In the **To Be Confirmed** tab, click an image to expand its labeling details. Check whether labeling information is correct, for example, whether the label is correct and whether the target bounding box is correctly added to the right position. If the auto labeling result is inaccurate, manually adjust the label or target bounding box and click **Labeled**. Then, the re-labeled data is displayed in the **Labeled** tab.

      If the target frame is in the incorrect position, the data need to be labeled again. Delete the original target frame. After manual adjustment, click **Labeled** to confirm the hard example.

   -  For labeling jobs of the image classification type

      In the **To Be Confirmed** tab, check whether labels added to images with the **Hard example** mark are correct. Select the images that are incorrectly labeled, delete the incorrect labels, and add correct labels in **Label** on the right. Click **OK**. The selected images and its labeling details are displayed in the **Labeled** tab.

      The selected images are incorrectly labeled. Delete the incorrect labels on the right, add a label in **Label**, and click **OK** to confirm the hard examples.

.. _en-us_topic_0000002340893858__en-us_topic_0000001185265241_en-us_topic_0217235047_section176081753173911:

Labeling Data in a Dataset as Hard Examples
-------------------------------------------

In a labeling job, labeled or unlabeled image data can be labeled as hard examples. Data labeled as hard examples can be used to improve model precision through built-in rules during subsequent model training.

#. Log in to the ModelArts management console. In the navigation pane, choose **Data Management** > **Label Data**. On the **Data Labeling** page, click **My Creations**.
#. In the labeling job list, select a labeling job of the object detection or image classification type and click the labeling job name to go to the labeling job details page.
#. On the labeling job details page, click the **Labeled**, **Unlabeled**, or **All** tab, select the images to be labeled as hard examples, and choose **Batch Process Hard Examples** > **Confirm Hard Example**. After the labeling is complete, a **Hard example** mark will be displayed in the upper right corner of a preview image.
