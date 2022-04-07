.. _modelarts_23_0021:

Deleting a Dataset
==================

If a dataset is no longer in use, you can delete it to release resources.

.. note::

   After a dataset is deleted, if you need to delete the data in the dataset input and output paths in OBS to release resources, delete the data and the OBS folders on the OBS Console.

Procedure
---------

#. In the left navigation pane, choose **Data Management > Datasets**. On the **Datasets** page, choose **More > Delete** in the **Operation** column of the dataset.
#. In the displayed dialog box, click **OK**.

   .. note::

      After a dataset is deleted, some functions such as dataset version management become unavailable. Exercise caution when performing this operation. However, the original data and labeling data of the dataset are still stored in OBS.
