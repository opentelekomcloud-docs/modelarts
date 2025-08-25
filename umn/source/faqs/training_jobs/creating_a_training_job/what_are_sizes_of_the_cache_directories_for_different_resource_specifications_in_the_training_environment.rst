:original_name: modelarts_05_0090.html

.. _modelarts_05_0090:

What Are Sizes of the /cache Directories for Different Resource Specifications in the Training Environment?
===========================================================================================================

When creating a training job, you can select CPU, or GPU resources based on the size of the training job.

ModelArts mounts a disk to **/cache**. You can use this directory to store temporary files. The **/cache** directory shares resources with the code directory. The directory has different capacities for different resource specifications.

-  GPU resources

   .. table:: **Table 1** Capacities of the cache directories for GPU resources

      ================== ========================
      GPU Specifications cache Directory Capacity
      ================== ========================
      V100               800 GB
      8*V100             3 TB
      P100               800 GB
      ================== ========================

-  CPU resources

   .. table:: **Table 2** Capacities of the cache directories for CPU resources

      ================== ========================
      CPU Specifications cache Directory Capacity
      ================== ========================
      2 vCPUs \| 8 GiB   50 GB
      8 vCPUs \| 32 GiB  50 GB
      ================== ========================
