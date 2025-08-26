:original_name: resmgmt-modelarts_0012.html

.. _resmgmt-modelarts_0012:

ModelArts Network
=================

ModelArts Network and VPC
-------------------------

ModelArts networks are used for interconnecting nodes in a ModelArts resource pool. You can only configure the name and CIDR block for a network. To ensure that there is no IP address segment in the CIDR block overlapped with that of the VPC to be accessed, multiple CIDR blocks are available for you to select.

A VPC provides a logically isolated virtual network for your instances. You can configure and manage the network as required. VPC provides logically isolated, configurable, and manageable virtual networks for cloud servers, cloud containers, and cloud databases. It helps you improve cloud service security and simplify network deployment.

Prerequisites
-------------

-  A VPC is available.
-  A subnet is available.

.. _en-us_topic_0000002340890628__en-us_topic_0143244658_section4115221610:

Creating a Network
------------------

#. Log in to the ModelArts management console. In the navigation pane, choose **Dedicated Resource Pools** > **Elastic Cluster**.
#. Click **Network** and then **Create**.
#. In the **Create Network** dialog box, set parameters.

   -  **Network Name**: customizable name
   -  **CIDR Block**: You can select **Preset** or **Custom**.

   .. note::

      -  Each user can create a maximum of 15 networks.
      -  Ensure there is no IP address segment in the CIDR block overlaps that of the VPC to be accessed. The CIDR block cannot be changed after the network is created. Possible conflict CIDR blocks are as follows:

         -  Your VPC CIDR block
         -  Container CIDR block (consistently to be 172.16.0.0/16)
         -  Service CIDR block (consistently to be 10.247.0.0/16)

#. Confirm the settings and click **OK**.

.. _en-us_topic_0000002340890628__section1473914311415:

(Optional) Interconnecting a VPC with a ModelArts Network
---------------------------------------------------------

VPC interconnection allows you to use resources across VPCs, improving resource utilization.

#. On the **Network** page, click **Interconnect VPC** in the **Operation** column of the target network.
#. In the displayed dialog box, click the button on the right of **Interconnect VPC**, and select an available VPC and subnet from the drop-down lists.

   .. note::

      The peer network to be interconnected cannot overlap with the current CIDR block.

   -  If no VPC is available, click **Create VPC** on the right to create a VPC.
   -  If no subnet is available, click **Create Subnet** on the right to create a subnet.

Deleting a Network
------------------

If a network is no longer needed for AI service development, you can delete the network.

#. Go to the **Network** tab and click **Delete** in the **Operation** column of a network.
#. Confirm the information and click **OK**.
