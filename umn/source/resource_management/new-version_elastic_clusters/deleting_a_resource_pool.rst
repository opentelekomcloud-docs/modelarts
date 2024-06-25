:original_name: resmgmt-modelarts_0010.html

.. _resmgmt-modelarts_0010:

Deleting a Resource Pool
========================

If a dedicated resource pool is no longer needed for AI service development, you can delete the resource pool to release resources.

.. note::

   After a dedicated resource pool is deleted, the development environments, training jobs, and inference services that depend on the resource pool are unavailable. A dedicated resource pool cannot be restored after being deleted.

#. Log in to the ModelArts management console. In the navigation pane, choose **Dedicated Resource Pools** > **Elastic Cluster**.

#. Locate the row that contains the target resource pool, choose **More** > **Delete** in the **Operation** column.

#. In the **Delete Dedicated Resource Pool** dialog box, enter **DELETE** in the text box and click **OK**.

   You can switch between tabs on the details page to view the training jobs and notebook instances created using the resource pool, and inference services deployed in the resource pool.
