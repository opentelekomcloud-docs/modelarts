:original_name: resmgmt-modelarts_0003.html

.. _resmgmt-modelarts_0003:

Resource Pool
=============

ModelArts Resource Pools
------------------------

When using ModelArts for AI development, you can use either of the following resource pools:

-  **Dedicated Resource Pool**: provides exclusive compute resources, which can be used for training jobs, model deployment, and DevEnviron instance delivery. It delivers more controllable resources and cannot be shared with other users. Before using a dedicated resource pool, create one and select it during AI development.
-  **Public Resource Pool**: provides large-scale public computing clusters, which are allocated based on job parameter settings. Resources are isolated by job. You can use ModelArts public resource pools to deliver training jobs, deploy models, or run DevEnviron instances and will be billed on a pay-per-use basis.

Differences Between Dedicated Resource Pools and Public Resource Pools
----------------------------------------------------------------------

-  Dedicated resource pools provide dedicated computing clusters and network resources for users. The dedicated resource pools of different users are physically isolated, while public resource pools are only logically isolated. Compared with public resource pools, dedicated resource pools feature better performance in isolation and security.
-  When a dedicated resource pool is used for creating jobs and the resources are sufficient, the jobs will not be queued. When a public resource pool is used for creating jobs, there is a high probability that the jobs will be queued.
-  A dedicated resource pool is accessible to your network. All running jobs in the pool can access storage and resources in your network. For example, if you select a dedicated resource pool with an accessible network when creating a training job, you can access SFS data after the training job is created.
-  Dedicated resource pools allow you to customize the runtime environment of physical nodes, for example, you can upgrade GPU or Ascend drivers. This function is not supported by public resource pools.

Differences Between New and Old Dedicated Resource Pools
--------------------------------------------------------

-  In the old version, the dedicated resource pools dedicated for development/training are separated from those dedicated for service deployment. In addition, the pools of the two types offer different functions and their user experience varies. In the new version, the dedicated resource pools of the two types are unified. You only need to configure one or multiple job types. Then, the dedicated resource pool automatically supports the configured job type.
-  New dedicated resource pools inherit all functions of the old ones and have greatly improved user experience in key functions such as purchasing and resizing a resource pool. Use new dedicated resource pools for smooth, transparent experience.
-  Additionally, the new dedicated resource pools offer enhanced functions, for example, allowing you to upgrade GPU or Ascend drivers, view details about job queuing, and use one network for multiple pools. More new functions of the new dedicated resource pools are coming soon.
