:original_name: modelarts_05_3155.html

.. _modelarts_05_3155:

What Do I Do If Resources Are Insufficient When a Real-Time Service Is Deployed, Started, Upgraded, or Modified?
================================================================================================================

Possible Cause
--------------

The configured instance specifications are beyond the specifications provided by the resource pool.

Solution
--------

When resources are insufficient, ModelArts retries for three times. If resources are released during these retries, the service can be successfully deployed.

If resources are still insufficient after three retries, the service deployment fails. In this case, perform the following operations to resolve this issue:

-  If the service is to be deployed in a public resource pool, wait until other users release resources.
-  If the service is to be deployed in a dedicated resource pool, select lower container specifications or custom specifications to deploy the service on the premise that the model requirements are met.
-  Expand the capacity of the current resource pool before deploying the service.
