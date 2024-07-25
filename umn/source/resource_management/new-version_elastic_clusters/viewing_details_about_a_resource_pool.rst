:original_name: resmgmt-modelarts_0005.html

.. _resmgmt-modelarts_0005:

Viewing Details About a Resource Pool
=====================================

#. Log in to the ModelArts management console. In the navigation pane, choose **Dedicated Resource Pools** > **Elastic Cluster**.
#. In the resource pool list, click a resource pool to go to its details page and view its information.

   -  If there are multiple resource pools, click |image1| in the upper left corner of the details page of one resource pool to switch between resource pools. Click **More** in the upper right corner to perform operations such as adjust capacity, delete the resource pool, or set the job type. The available operations vary depending on resource pools.
   -  In the **Network** area of **Basic Information**, you can click the number of resource pools associated to view associated resource pools.
   -  In the extended information area, you can view the monitoring, jobs, nodes, specifications, events, and subpools. For details, see the following section.

Viewing Resource Pool Monitoring Information
--------------------------------------------

On the resource pool details page, click **Monitoring**. The resource usage including used CPUs, memory usage, and available disk capacity of the resource pool is displayed. If AI accelerators are used in the resource pool, the GPU and NPU monitoring information is also displayed.

Viewing Resource Pool Jobs
--------------------------

On the resource pool details page, click **Jobs**. You can view all jobs running in the resource pool. If a job is queuing, you can view its queuing position.

.. note::

   Only training jobs can be viewed.

Viewing Resource Pool Nodes
---------------------------

On the resource pool details page, click **Nodes**. You can view all nodes in the resource pool and the resource usage of each node.

Some resources are reserved for cluster components. Therefore, **CPUs (Available/Total)** does not indicate the number of physical resources on the node. It only displays the number of resources that can be used by services. CPU cores are metered in milicores, and 1000 milicores equal 1 physical core.

-  Deleting nodes:

   On the **Nodes** tab page, click |image2| in the **Operation** column to delete a node.

-  Processing abnormal nodes:

   Delete abnormal nodes in a resource pool one by one or in a batch and add new ones for substitution.

.. note::

   Before deleting a node, ensure that there are no running jobs on this node. Otherwise, the jobs will be interrupted.

   If there is only one node, it cannot be deleted.

Viewing Resource Pool Specifications
------------------------------------

On the resource pool details page, click **Specifications**. You can view the specifications used by the resource pool and the number of each specification.

Viewing Resource Pool Events
----------------------------

On the resource pool details page, click **Events**. You can view all events of the resource pool. The cause of an event is **PoolStatusChange** or **PoolResourcesStatusChange**.

On the trace list, click |image3| on the right of **Event Type** to filter events.

-  When a resource pool starts to be created or becomes abnormal, the resource pool status changes and the change will be recorded as an event.
-  When the number of nodes that are available or abnormal or in the process of being created or deleted changes, the resource pool node status changes and the change will be recorded as an event.

.. |image1| image:: /_static/images/en-us_image_0000001910023346.png
.. |image2| image:: /_static/images/en-us_image_0000001943982549.png
.. |image3| image:: /_static/images/en-us_image_0000001910023338.png
