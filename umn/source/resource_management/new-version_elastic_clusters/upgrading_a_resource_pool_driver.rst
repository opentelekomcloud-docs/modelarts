:original_name: resmgmt-modelarts_0009.html

.. _resmgmt-modelarts_0009:

Upgrading a Resource Pool Driver
================================

Description
-----------

If GPUs resources are used in a dedicated resource pool, you may need to customize GPU drivers. ModelArts allows you to upgrade GPU drivers of your dedicated resource pools.

There are two driver upgrade modes: secure upgrade and forcible upgrade.

-  Secure upgrade: Running services are not affected. After the upgrade starts, the nodes are isolated (new jobs cannot be delivered). After the existing jobs on the nodes are complete, the upgrade is performed. The secure upgrade may take a long time because the jobs must be completed first.
-  Forcible upgrade: The drivers are directly upgraded, regardless of whether there are running jobs.

Constraints
-----------

The target dedicated resource pool is in running, and the resource pool contains GPU resources.

Upgrading the Driver
--------------------

#. Log in to the ModelArts management console. In the navigation pane, choose **Dedicated Resource Pools** > **Elastic Cluster**.
#. In the **Operation** column of the target resource pool, choose **More** > **Upgrade Driver**.
#. In the **Upgrade Driver** dialog box, the driver type, number of nodes, current version, target version, and upgrade mode of the dedicated resource pool are displayed.

   -  **Target Version**: Select a target driver version from the drop-down list.
   -  **Upgrade Mode**: Select **Secure upgrade** or **Forcible upgrade**.

#. Click **OK** to start the driver upgrade.
