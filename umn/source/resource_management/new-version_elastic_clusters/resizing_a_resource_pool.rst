:original_name: resmgmt-modelarts_0006.html

.. _resmgmt-modelarts_0006:

Resizing a Resource Pool
========================

Description
-----------

The demand for resources in a dedicated resource pool may change due to the changes of AI development services. In this case, you can add or delete nodes in your dedicated resource pool.

-  You can add nodes of existing flavors in the resource pool or add flavors to scaling out a resource pool.
-  You can delete nodes of existing flavors in the resource pool or delete flavors to scaling in a resource pool. You cannot delete all flavors when you resize a resource pool. To delete all flavors, see :ref:`Deleting a Resource Pool <resmgmt-modelarts_0010>`.

.. note::

   Before scaling in a resource pool, ensure that there are no services running in the pool. Alternatively, switch to the details page of the target resource pool, delete the nodes where no services are running to scale in the pool. Otherwise, the services will be interrupted.

Constraints
-----------

-  Only dedicated resource pool in the **Running** status can be scaled in or out.
-  You cannot add nodes for a flavor and delete nodes for another flavor at the same time.

Resizing a Dedicated Resource Pool
----------------------------------

A resource pool can be resized by adjusting the number of nodes of existing flavors or adding or deleting flavors.

#. Log in to the ModelArts management console. In the navigation pane, choose **Dedicated Resource Pools** > **Elastic Cluster**.

   .. note::

      A resource pool is suspended when it is migrated from the old version to the new version. You cannot adjust the capacity of such a resource pool or unsubscribe from it.

#. Add or delete nodes.

   Click **Adjust Capacity** in the **Operation** column of the target resource pool.

   In the **Resource Configurations** area, set **AZ** to **Automatically allocated** or **Specifies AZ**. Click **Submit** and then **OK** to save the changes.

   -  If **AZ** is set to **Automatically allocated**, you can increase or decrease the number of nodes to scale out or in the resource pool. After the scaling, nodes are automatically allocated to AZs.
   -  If you select **Specifies AZ**, you can allocate nodes to different AZs.

#. Add or delete flavors.

   Choose **More** > **Adjust Flavors** in the **Operation** column of the target resource pool to add or delete the flavors of the physical resource pool. On the **Scale In/Out Dedicated Resource Pool** page, you can add or delete a flavor.

   -  On the **Scale In/Out Dedicated Resource Pool** page, click **Add Specifications** and set the flavor type, AZ, and node quantity. Confirm the configuration and click **Submit** to add the flavor.
   -  On the **Scale In/Out Dedicated Resource Pool** page, click |image1| on the right of the target flavor panel to delete the flavor. Confirm the configuration and click **Submit** to delete the flavor.

      .. note::

         When you delete a flavor, the resource pool nodes of the flavor will be deleted accordingly and cannot be restored.

.. |image1| image:: /_static/images/en-us_image_0000002374848901.png
