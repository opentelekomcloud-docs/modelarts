:original_name: modelarts_05_3157.html

.. _modelarts_05_3157:

How Do I Select Compute Node Specifications for Deploying a Service?
====================================================================

Before deploying a service, specify node specifications. The node specifications displayed on the GUI are calculated by ModelArts based on the target AI application and the node specifications available in the resource pool. You can select the specifications provided by ModelArts or customize the specifications (supported only in dedicated resource pools).

Selecting compute node specifications based on the resources required by your AI application. For example, if an AI application requires 3 CPUs and 10 GB of memory, select compute node specifications higher than 3 CPUs and 10 GB of memory. This ensures that the service can be successfully deployed and run properly.

When using compute node specifications, pay attention to the following:

**Permission control**

Permissions on general-purpose compute node specifications, for example, **modelarts.vm.cpu.2u** are not controlled. You can select the specifications as long as there are idle resources in the resource pool. ModelArts provides two specifications by default, CPU-powered **modelarts.vm.cpu.2u** and GPU-powered **modelarts.vm.gpu.p4**.

For some special specifications, contact the system administrator to request for permissions.

**Specifications sold out in a public resource pool**

Resources in a public resource pool are limited. If a specification is displayed as sold out, resources of the current specification have been used up. In this case, select other specifications or create your own dedicated resource pool.

**Custom specifications**

You can customize resource specifications only when a dedicated resource pool is used. Specifications cannot be customized in public resource pools.
