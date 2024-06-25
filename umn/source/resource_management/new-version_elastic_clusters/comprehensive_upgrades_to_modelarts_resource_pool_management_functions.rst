:original_name: resmgmt-modelarts_0002.html

.. _resmgmt-modelarts_0002:

Comprehensive Upgrades to ModelArts Resource Pool Management Functions
======================================================================

ModelArts dedicated resource pools have been upgraded. In the new system, there are only unified ModelArts dedicated resource pools, which are no longer classified as the pools dedicated for development/training and the pools dedicated for service deployment. The new-version dedicated resource pools support flexible configuration of job types, and allow you to manage networks and interconnect VPCs with the networks.

The new dedicated resource pool management page provides more comprehensive functions and displays more information about the resource pools. More details about how to use and manage dedicated resource pools are provided in subsequent sections of this document. If you are new to ModelArts dedicated resource pools, try new-version dedicated resource pools. If you have used ModelArts dedicated resource pools, the old-version pools will be smoothly switched to new-version pools.

Read the following contents to learn about new-version dedicated resource pools.

Features of New-Version Dedicated Resource Pools
------------------------------------------------

The new-version dedicated resource pool management is a comprehensive technology and product improvement. The main improvements are as follows:

-  **Single dedicated resource pool type for diverse purposes**: Dedicated resource pools are no longer classified into those for development/training and those for service deployment. You can run both training and inference workloads in a dedicated resource pool. You can also set the job types supported by a dedicated resource pool based on your needs.
-  **Dedicated resource pool network connection**: You can create and manage dedicated resource pool networks on the ModelArts management console. If you need to access resources in your VPC for jobs running in a dedicated resource pool, interconnect the VPC with the dedicated resource pool network.
-  **More cluster details**: The new-version dedicated resource pool details page provides more cluster details, such as jobs, nodes, and resource monitoring, helping you learn about the cluster status and better plan and use resources.
-  **Cluster GPU/NPU driver management**: On the new-version dedicated resource pool details page, you can select an accelerator card driver and perform change upon submission or smooth upgrade of the driver based on service requirements.
-  **Fine-grained resource allocation (coming soon)**: You can divide your dedicated resource pool into multiple small pools and assign different quotas and permissions to each small pool for flexible and refined resource allocation and management.

More features will be provided in later versions for a better user experience.

Can I Continue to Use the Existing Dedicated Resource Pools After the Upgrade Takes Effect?
-------------------------------------------------------------------------------------------

If you have created dedicated resource pools, you can still access the old-version dedicated resource pool management page on the ModelArts management console and use the created resource pools, but you cannot create dedicated resource pool on that page. ModelArts allows you to migrate existing dedicated resource pools to the new management page. You will be contacted to complete the migration and this does not require you to perform any operations. In addition, the migration does not affect the workloads running in the dedicated resource pools. Pay attention to the easy-to-use new management functions of dedicated resource pools. There is no change in creating training jobs or inference services.

How Can I Get Help or Provide Feedback if I Encounter Problems During Use?
--------------------------------------------------------------------------

Similar to other ModelArts functions, you can report problems or obtain help in the sidebar of the console. In addition, you are advised to read the subsequent sections of this document to further understand how to use ModelArts dedicated resource pools.

Instructions of Dedicated Resource Pools
----------------------------------------

-  If you are using dedicated resource pools for the first time, get started by reading :ref:`Resource Pool <resmgmt-modelarts_0003>`.
-  Create a dedicated resource pool by referring to :ref:`Creating a Resource Pool <resmgmt-modelarts_0004>`.
-  View the details about a created dedicated resource pool by referring to :ref:`Viewing Details About a Resource Pool <resmgmt-modelarts_0005>`.
-  If the specifications of a dedicated resource pool do not meet your service requirements, adjust the specifications by referring to :ref:`Resizing a Resource Pool <resmgmt-modelarts_0006>`.
-  Set or change job types supported by a dedicated resource pool by referring to :ref:`Changing Job Types Supported by a Resource Pool <resmgmt-modelarts_0008>`.
-  Upgrade the GPU/Ascend driver of your dedicated resource pools by referring to :ref:`Upgrading a Resource Pool Driver <resmgmt-modelarts_0009>`.
-  If a dedicated resource pool is no longer needed, delete it by referring to :ref:`Deleting a Resource Pool <resmgmt-modelarts_0010>`.
-  If any exception occurs when you use a dedicated resource pool, handle the exception by referring to :ref:`Abnormal Status of a Dedicated Resource Pool <resmgmt-modelarts_0011>`.
-  Manage dedicated resource pool networks or interconnect VPCs with the networks by referring to :ref:`ModelArts Network <resmgmt-modelarts_0012>`.
