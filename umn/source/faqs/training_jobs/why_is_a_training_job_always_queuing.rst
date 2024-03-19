:original_name: modelarts_05_0363.html

.. _modelarts_05_0363:

Why Is a Training Job Always Queuing?
=====================================

If the training job is always queuing, the selected resources are limited in the resource pool, and the job needs to be queued. In this case, wait for resources. To speed up resource obtaining, do as follows:

#. If you use a public resource pool:

   Resources in a public resource pool are limited. During peak hours, resources may be insufficient if service traffic is heavy. Try to take the following measures:

   -  If a free flavor was used, change it to a charged one. Few resources are provided for free flavors, leading to a high queuing probability.
   -  The less number of cards in the selected flavor leads to the lower queuing probability. For example, the probability of queuing when selecting a 1-card flavor is much less than that of queuing when selecting an 8-card flavor.
   -  Switch to another region.
   -  If resources will be used for a long term, purchase a dedicated resource pool.

#. If you use a dedicated resource pool:

   -  If there are multiple available dedicated resource pools, switch to an idle one.
   -  Release resources in the current resource pool, for example, stop notebook instances that are not used for a long time.
   -  Submit a training job during off-peak hours.
   -  Contact the account administrator of the dedicated resource pool to expand the resource pool based on the resource usage.
