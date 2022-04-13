.. _modelarts_21_0033:

How Do I Perform Incremental Training in an ExeML Project?
==========================================================

Each round of training generates a training version in an ExeML project. If a training result is unsatisfactory (for example, if the precision is not good enough), you can add high-quality data or add or delete labels, and perform training again.

.. note::

   -  For better training results, use high-quality data for incremental training to improve data labeling performance.

Incremental Training Procedure
------------------------------

#. Log in to the ModelArts console, and click **ExeML** in the left navigation pane.

#. On the **ExeML** page, click a project name. The ExeML details page of the project is displayed.

#. On the **Label Data** page, click the **Unlabeled** tab. On the **Unlabeled** tab page, you can add images or add or delete labels.

   If you add images, label the added images again. If you add or delete labels, check all images and label them again. You also need to check whether new labels need to be added for the labeled data.

#. After all images are labeled, click **Train** in the upper right corner. In the **Training Configuration** dialog box that is displayed, set **Incremental Training Version** to the training version that has been completed to perform incremental training based on this version. Set other parameters as prompted.

   After the settings are complete, click **Yes** to start incremental training. The system automatically switches to the **Train Model** page. After the training is complete, you can view the training details, such as training precision, evaluation result, and training parameters.
