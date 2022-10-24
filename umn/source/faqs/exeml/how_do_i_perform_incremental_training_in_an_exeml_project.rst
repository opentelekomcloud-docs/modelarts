:original_name: modelarts_21_0060.html

.. _modelarts_21_0060:

How Do I Perform Incremental Training in an ExeML Project?
==========================================================

Each round of training generates a training version in an ExeML project. If a training result is unsatisfactory (for example, unsatisfactory about the training precision), you can add high-quality data or add or delete labels, and perform training again.

.. note::

   -  Currently, incremental training is only available for the following types of ExeML projects: image classification and object detection.
   -  For better training results, you are advised to use high-quality data for incremental training to improve data labeling performance.

Incremental Training Procedure
------------------------------

#. Log in to the ModelArts management console, and click **ExeML** in the left navigation pane.

#. On the **ExeML** page, click a project name. The ExeML details page of the project is displayed.

#. On the **Label Data** page, click the **Unlabeled** tab. On the **Unlabeled** tab page, you can add images or add or delete labels.

   If you add images, you need to label the added images again. If you add or delete labels, you are advised to check all images and label them again. You also need to check whether new labels need to be added for the labeled data.

#. After all images are labeled, click **Train** in the upper right corner. In the **Training Configuration** dialog box that is displayed, set **Incremental Training Version** to the training version that has been completed to perform incremental training based on this version. Set other parameters as prompted.

   After the settings are complete, click **Yes** to start incremental training. The system automatically switches to the **Train Model** page. After the training is complete, you can view the training details, such as training precision, evaluation result, and training parameters.


   .. figure:: /_static/images/en-us_image_0000001279536749.png
      :alt: **Figure 1** Selecting an incremental training version

      **Figure 1** Selecting an incremental training version
