:original_name: modelarts_23_0076.html

.. _modelarts_23_0076:

Resource Pools
==============

ModelArts Resource Pools
------------------------

When using ModelArts to implement AI Development Lifecycle, you can use two different resource pools to train and deploy models.

-  **Public Resource Pool**: provides public large-scale computing clusters, which are allocated based on job parameter settings. Resources are isolated by job.

-  **Dedicated Resource Pool**: provides exclusive compute resources, which can be used for model deployment. It delivers higher efficiency and cannot be shared with other users.

   Create a dedicated resource pool and select the dedicated resource pool during AI development. For details about the dedicated resource pool, see the following:

   :ref:`Dedicated Resource Pool <modelarts_23_0076__en-us_topic_0143244658_section1072918334226>`

   :ref:`Creating a Dedicated Resource Pool <modelarts_23_0076__en-us_topic_0143244658_section4115221610>`

   :ref:`Scaling a Dedicated Resource Pool <modelarts_23_0076__en-us_topic_0143244658_section1521854122017>`

   :ref:`Deleting a Dedicated Resource Pool <modelarts_23_0076__en-us_topic_0143244658_section102631431172915>`

.. _modelarts_23_0076__en-us_topic_0143244658_section1072918334226:

Dedicated Resource Pool
-----------------------

-  Dedicated resource pools can be used in the following jobs and tasks: deployment (including real-time services).
-  Dedicated resource pools are available only when they are in the **Running** status. If a dedicated resource pool is **Unavailable** or **Abnormal**, rectify the fault before using it.

.. _modelarts_23_0076__en-us_topic_0143244658_section4115221610:

Creating a Dedicated Resource Pool
----------------------------------

#. Log in to the ModelArts management console and choose **Dedicated Resource Pools** on the left.

#. On the **Dedicated Resource Pools** page, the list of the created resource pools is displayed.

#. Click **Create** in the upper left corner. The page for creating a dedicated resource pool is displayed.

#. Set the parameters on the page. For details about how to set parameters, see :ref:`Table 1 <modelarts_23_0076__en-us_topic_0143244658_table199892206411>`.

   .. _modelarts_23_0076__en-us_topic_0143244658_table199892206411:

   .. table:: **Table 1** Parameters of the **Dedicated for Service Deployment** type

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                        |
      +===================================+====================================================================================================================================================================================================================================================================================================================================+
      | Resource Type                     | The default value is **Dedicated for Service Deployment** and cannot be changed.                                                                                                                                                                                                                                                   |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Billing Mode                      | Select a billing mode, **Yearly/Monthly** or **Pay-per-use**. The **Yearly/Monthly** billing mode is supported only in CN North-Beijing4.                                                                                                                                                                                          |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                              | Name of a dedicated resource pool.                                                                                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                                                    |
      |                                   | The value can contain letters, digits, hyphens (-), and underscores (_).                                                                                                                                                                                                                                                           |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Brief description of a dedicated resource pool.                                                                                                                                                                                                                                                                                    |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Custom Network Configuration      | If you enable **Custom Network Configuration**, the service instance runs on the specified network and can communicate with other cloud service resource instances on the network. If you do not enable **Custom Network Configuration**, ModelArts allocates a dedicated network to each user and isolates users from each other. |
      |                                   |                                                                                                                                                                                                                                                                                                                                    |
      |                                   | If you enable **Custom Network Configuration**, set **VPC**, **Subnet**, and **Security Group**. If no network is available, go to the VPC service and create a network. For details, see `Virtual Private Cloud User Guide <https://docs.otc.t-systems.com/usermanual/vpc/en-us_topic_0013935842.html>`__.                        |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | AZ                                | You can select **Random**, **AZ 1**, **AZ 2**, or **AZ 3** based on site requirements. An AZ is a physical region where resources use independent power supplies and networks. AZs are physically isolated but interconnected through an internal network. To enhance workload availability, create nodes in different AZs.        |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Nodes                             | Select the number of nodes in a dedicated resource pool. More nodes mean higher computing performance.                                                                                                                                                                                                                             |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Specifications                    | Required specifications. The GPU delivers better performance, and the CPU is more cost-effective.                                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                                                                    |
      |                                   | -  CPU: **modelarts.vm.cpu.8ud**                                                                                                                                                                                                                                                                                                   |
      |                                   | -  GPU: **modelarts.vm.gpu.16g.v100**                                                                                                                                                                                                                                                                                              |
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

If a dedicated resource pool is no longer needed during AI service development, you can delete the resource pool to release resources and reduce costs.

.. note::

   -  After a dedicated resource pool is deleted, the training jobs, notebook instances, and deployment that depend on the resource pool are unavailable. A dedicated resource pool cannot be restored after being deleted. Exercise caution when deleting a dedicated resource pool.

#. Go to the dedicated resource pool management page, locate the row that contains the desired dedicated resource pool, and click **Delete** in the **Operation** column.
#. In the dialog box that is displayed, click **OK**.
