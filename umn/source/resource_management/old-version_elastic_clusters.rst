:original_name: modelarts_23_0076.html

.. _modelarts_23_0076:

Old-Version Elastic Clusters
============================

ModelArts Resource Pools
------------------------

When using ModelArts for full-process AI development, you can use two different resource pools.

-  **Public Resource Pool**: provides public large-scale computing clusters, which are allocated based on job parameter settings. Resources are isolated by job.

-  **Dedicated Resource Pool**: provides exclusive compute resources, which can be used for model deployment. It delivers higher efficiency and cannot be shared with other users.

   Create a dedicated resource pool and select the dedicated resource pool during AI development. For details about the dedicated resource pool, see the following:

   :ref:`Dedicated Resource Pools <en-us_topic_0000002340728224__section6250135125515>`

   :ref:`Creating a Dedicated Resource Pool <en-us_topic_0000002340728224__section4115221610>`

   :ref:`Scaling a Dedicated Resource Pool <en-us_topic_0000002340728224__section1521854122017>`

   :ref:`Deleting a Dedicated Resource Pool <en-us_topic_0000002340728224__section102631431172915>`

.. _en-us_topic_0000002340728224__section6250135125515:

Dedicated Resource Pools
------------------------

-  Dedicated resource pools can be used by notebook instances, training jobs, or for model deployment.
-  Dedicated resource pools are classified into two types: **Dedicated for Development/Training** and **Dedicated for Service Deployment**. The **Dedicated for Development/Training** type can be used only for notebook instances and training. The **Dedicated for Service Deployment** type can be used only for Model deployment.
-  Dedicated resource pools are available only when they are in the **Running** state. If a dedicated resource pool is unavailable or abnormal, rectify the fault before using it.

.. _en-us_topic_0000002340728224__section4115221610:

Creating a Dedicated Resource Pool
----------------------------------

#. Log in to the ModelArts management console. In the navigation pane, choose **Dedicated Resource Pools > Elastic Cluster**.

#. On the **Dedicated Resource Pools** page, select **Dedicated for Development/Training** or **Dedicated for Service Deployment**.

#. Click **Create** in the upper left corner. The page for creating a dedicated resource pool is displayed.

#. Set the parameters on the page. For details about how to set parameters, see :ref:`Table 1 <en-us_topic_0000002340728224__table1073325155617>` and :ref:`Table 2 <en-us_topic_0000002340728224__table199892206411>`.

   .. _en-us_topic_0000002340728224__table1073325155617:

   .. table:: **Table 1** Parameters of the **Dedicated for Development/Training** type

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                           |
      +===================================+=======================================================================================================================================================================================================+
      | Resource Type                     | The default value is and cannot be changed.                                                                                                                                                           |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                              | Name of a dedicated resource pool.                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                       |
      |                                   | The value can contain letters, digits, hyphens (-), and underscores (_).                                                                                                                              |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Brief description of a dedicated resource pool.                                                                                                                                                       |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Nodes                             | Select the number of nodes in a dedicated resource pool. More nodes mean higher computing performance.                                                                                                |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Specifications                    | Required specifications. The GPU delivers better performance, and the CPU is more cost-effective. If a flavor is sold out, you can purchase it again only after other users delete the resource pool. |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _en-us_topic_0000002340728224__table199892206411:

   .. table:: **Table 2** Parameters of the **Dedicated for Service Deployment** type

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                        |
      +===================================+====================================================================================================================================================================================================================================================================================================================================+
      | Resource Type                     | The default value is **Dedicated for Service Deployment** and cannot be changed.                                                                                                                                                                                                                                                   |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                              | Name of a dedicated resource pool.                                                                                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                                                    |
      |                                   | Enter 4 to 24 characters starting with a lowercase letter and not ending with a hyphen (-). Only lowercase letters, digits, and hyphens (-) are allowed.                                                                                                                                                                           |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Brief description of a dedicated resource pool.                                                                                                                                                                                                                                                                                    |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Custom Network Configuration      | If you enable **Custom Network Configuration**, the service instance runs on the specified network and can communicate with other cloud service resource instances on the network. If you do not enable **Custom Network Configuration**, ModelArts allocates a dedicated network to each user and isolates users from each other. |
      |                                   |                                                                                                                                                                                                                                                                                                                                    |
      |                                   | If you enable **Custom Network Configuration**, set **VPC**, **Subnet**, and **Security Group**. If no network is available, go to the VPC service and create a network.                                                                                                                                                           |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | AZ                                | You can select **Random**, **AZ 1**, **AZ 2**, or **AZ 3** based on site requirements. An AZ is a physical region where resources use independent power supplies and networks. AZs are physically isolated but interconnected through an internal network. To enhance workload availability, create nodes in different AZs.        |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Nodes                             | Select the number of nodes in a dedicated resource pool. More nodes mean higher computing performance.                                                                                                                                                                                                                             |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Specifications                    | Required specifications. The GPU delivers better performance.                                                                                                                                                                                                                                                                      |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. After confirming that the specifications are correct, create a dedicated resource pool as prompted. After a dedicated resource pool is created, its status changes to **Running**.

   .. important::

      A newly purchased dedicated resource pool can be used only after its development environment is initialized.

(Optional) Interconnecting a VPC
--------------------------------

After a resource pool is created, you can interconnect a VPC on the resource pool details page. The procedure is as follows:

.. note::

   Only resource pools dedicated for development/training can be interconnected with a VPC.

#. On the **Dedicated Resource Pools** page, click the target resource pool.
#. On the dedicated resource pool details page, click **Configure NAS VPC**.
#. On the **Configure NAS VPC** page, enable **NAS VPC Connection** and set **NAS VPC** and **NAS Subnet**.

   -  If no VPC is available, click **Create VPC** on the right to create a VPC.
   -  If no subnet is available, click **Create Subnet** on the right to create a subnet.

#. Click **OK**.

.. _en-us_topic_0000002340728224__section1521854122017:

Scaling a Dedicated Resource Pool
---------------------------------

After a dedicated resource pool is used for a period of time, you can scale out or in the capacity of the resource pool by increasing or decreasing the number of nodes.

The procedure for scaling is as follows:

#. Go to the dedicated resource pool management page, locate the row that contains the desired dedicated resource pool, and click **Scale** in the **Operation** column.
#. On the scaling page, increase or decrease the number of nodes. Increasing the node quantity scales out the resource pool whereas decreasing the node quantity scales in the resource pool. Scale the capacity based on service requirements.

   -  During capacity expansion, increase the number of nodes based on your service needs.
   -  During capacity reduction, delete the target nodes in the **Operation** column. To reduce one node, switch off the node in **Node List** to delete the node.

      .. caution::

         Before reducing the capacity of a resource pool for real-time inference, ensure that there are no running instances on the nodes to be released. Otherwise, the real-time services will be interrupted. If you are not sure whether any instance is running on the node to be released, submit a consultation service ticket.

#. Click **Submit**. After the request is submitted, the dedicated resource pool management page is displayed.

   .. note::

      The node is not deleted immediately after the request is submitted. In this case, do not delete nodes from the dedicated resource pool list. Otherwise, the deletion may fail.

      You can view the event list on the dedicated resource pool details page. "Begin to delete resource node %s" indicates that the node deletion starts. "Resource node %s deleted" indicates that the node has been deleted in the background.

.. _en-us_topic_0000002340728224__section102631431172915:

Deleting a Dedicated Resource Pool
----------------------------------

If a dedicated resource pool is no longer needed for AI service development, you can delete the resource pool to release resources.

.. note::

   -  After a dedicated resource pool is deleted, the training jobs, notebook instances, real-time services, and batch services that depend on the resource pool will become unavailable. A dedicated resource pool cannot be restored after being deleted. Exercise caution when performing this operation.

#. Go to the dedicated resource pool management page and release resources.
