:original_name: modelarts_23_0223.html

.. _modelarts_23_0223:

Confirming Hard Examples
========================

.. note::

   Only datasets of image classification and object detection types support the auto hard example detection function.

Labeling Data in a Dataset as Hard Examples
-------------------------------------------

In a dataset, labeled or unlabeled image data can be labeled as hard examples. Data labeled as hard examples can be used to improve model precision through built-in rules during subsequent model training.

#. Log in to the ModelArts management console. In the left navigation pane, choose **Data Management** > **Datasets**. The **Datasets** page is displayed.
#. In the dataset list, select the dataset of the object detection or image classification type and click the dataset name to go to the **Dashboard** tab page of the dataset.
#. On the **Dashboard** page of the dataset, click **Label** in the upper right corner. The dataset details page is displayed.
#. On the dataset details page, click the **Labeled**, **Unlabeled**, or **All** tab, select the images to be labeled as hard examples, and choose **Batch process Hard Examples** > **Confirm Hard Example**. After the labeling is complete, a **Hard example** mark will be displayed in the upper right corner of a preview image.
