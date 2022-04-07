.. _modelarts_23_0076:

Resource Pools
==============

ModelArts Resource Pools
------------------------

When using ModelArts to implement AI Development Lifecycle, you can use two different resource pools to train and deploy models.

-  **Public Resource Pool**: provides public large-scale computing clusters, which are allocated based on job parameter settings. Resources are isolated by job.

-  **Dedicated Resource Pool**: provides exclusive compute resources, which can be used for model deployment. It delivers higher efficiency and cannot be shared with other users.

   Create a dedicated resource pool and select the dedicated resource pool during AI development. For details about the dedicated resource pool, see the following:

   :ref:`Dedicated Resource Pool <modelarts_23_0076__en-us_topic_0143244658_section6250135125515>`

   :ref:`Creating a Dedicated Resource Pool <modelarts_23_0076__en-us_topic_0143244658_section4115221610>`

   :ref:`Scaling a Dedicated Resource Pool <modelarts_23_0076__en-us_topic_0143244658_section1521854122017>`

   :ref:`Deleting a Dedicated Resource Pool <modelarts_23_0076__en-us_topic_0143244658_section102631431172915>`

.. _modelarts_23_0076__en-us_topic_0143244658_section6250135125515:

Dedicated Resource Pool
-----------------------

-  Dedicated resource pools can be used in the following jobs and tasks: notebook instances, training, TensorBoard, and deployment.
-  Dedicated resource pools are classified into two types: **Dedicated for Development/Training** and **Dedicated for Service Deployment**. The **Dedicated for Development/Training** type can be used only for notebook instances, training, and TensorBoard. The **Dedicated for Service Deployment** type can be used only for model deployment.
-  Dedicated resource pools are available only when they are in the **Running** status. If a dedicated resource pool is unavailable or abnormal, rectify the fault before using it.

.. _modelarts_23_0076__en-us_topic_0143244658_section4115221610:

Creating a Dedicated Resource Pool
----------------------------------

#. Log in to the ModelArts management console and choose **Dedicated Resource Pools** on the left.

#. On the **Dedicated Resource Pools** page, select **Dedicated for Development/Training** or **Dedicated for Service Deployment**.

#. Click **Create** in the upper left corner. The page for creating a dedicated resource pool is displayed.

#. Set the parameters on the page. For details about how to set parameters, see :ref:`Table 1 <modelarts_23_0076__en-us_topic_0143244658_table1073325155617>` and :ref:`Table 2 <modelarts_23_0076__en-us_topic_0143244658_table199892206411>`.

   .. _modelarts_23_0076__en-us_topic_0143244658_table1073325155617:

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

   .. _modelarts_23_0076__en-us_topic_0143244658_table199892206411:

   .. table:: **Table 2** Parameters of the **Dedicated for Service Deployment** type

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                        |
      +===================================+====================================================================================================================================================================================================================================================================================================================================+
      | Resource Type                     | The default value is **Dedicated for Service Deployment** and cannot be changed.                                                                                                                                                                                                                                                   |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                              | Name of a dedicated resource pool.                                                                                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                                                    |
      |                                   | The value can contain letters, digits, hyphens (-), and underscores (_).                                                                                                                                                                                                                                                           |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Brief description of a dedicated resource pool.                                                                                                                                                                                                                                                                                    |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Custom Network Configuration      | If you enable **Custom Network Configuration**, the service instance runs on the specified network and can communicate with other cloud service resource instances on the network. If you do not enable **Custom Network Configuration**, ModelArts allocates a dedicated network to each user and isolates users from each other. |
      |                                   |                                                                                                                                                                                                                                                                                                                                    |
      |                                   | If you enable **Custom Network Configuration**, set **VPC**, **Subnet**, and **Security Group**. If no network is available, go to the VPC service and create a network. .                                                                                                                                                         |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | AZ                                | You can select **Random**, **AZ 1**, **AZ 2**, or **AZ 3** based on site requirements. An AZ is a physical region where resources use independent power supplies and networks. AZs are physically isolated but interconnected through an internal network. To enhance workload availability, create nodes in different AZs.        |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Nodes                             | Select the number of nodes in a dedicated resource pool. More nodes mean higher computing performance.                                                                                                                                                                                                                             |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Specifications                    | Required specifications. The GPU delivers better performance.                                                                                                                                                                                                                                                                      |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. After confirming that the specifications are correct, create a dedicated resource pool as prompted. After a dedicated resource pool is created, its status changes to **Running**.

.. _modelarts_23_0076__en-us_topic_0143244658_section1521854122017:

Scaling a Dedicated Resource Pool
---------------------------------

After a dedicated resource pool is used for a period of time, you can scale out or in the capacity of the resource pool by increasing or decreasing the number of nodes.

The procedure for scaling is as follows:

#. Go to the dedicated resource pool management page, locate the row that contains the desired dedicated resource pool, and click **Scale** in the **Operation** column.
#. On the scaling page, increase or decrease the number of nodes. Increasing the node quantity scales out the resource pool whereas decreasing the node quantity scales in the resource pool. Scale the capacity based on service requirements.

   -  During capacity expansion,
   -  During capacity reduction, delete the target nodes in the **Operation** column. To reduce one node, you need to switch off the node in **Node List** to delete the node.

#. Click **Submit**. After the request is submitted, the dedicated resource pool management page is displayed.

.. _modelarts_23_0076__en-us_topic_0143244658_section102631431172915:

Deleting a Dedicated Resource Pool
----------------------------------

If a dedicated resource pool is no longer needed during AI service development, you can delete the resource pool to release resources.

.. note::

   -  After a dedicated resource pool is deleted, the training jobs, notebook instances, and deployment that depend on the resource pool are unavailable. A dedicated resource pool cannot be restored after being deleted. Exercise caution when deleting a dedicated resource pool.

#. Go to the dedicated resource pool management page, locate the row that contains the desired dedicated resource pool, and click **Delete** in the **Operation** column.
#. In the dialog box that is displayed, click **OK**.
