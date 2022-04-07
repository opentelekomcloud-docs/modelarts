.. _modelarts_05_0090:

What Are Sizes of the /cache Directories for Different Resource Specifications in the Training Environment?
===========================================================================================================

When creating a training job, you can select CPU, GPU, or Ascend resources based on the size of the training job.

ModelArts mounts the disk to the **/cache** directory. You can use this directory to store temporary files. The **/cache** directory shares resources with the code directory. The directory has different capacities for different resource specifications.

-  GPU resources

   .. table:: **Table 1** Capacities of the cache directories for GPU resources

      ================== ========================
      GPU Specifications cache Directory Capacity
      ================== ========================
      V100               800G
      8*V100             3T
      P100               800G
      ================== ========================

-  CPU resources

   .. table:: **Table 2** Capacities of the cache directories for CPU resources

      ================== ========================
      CPU Specifications cache Directory Capacity
      ================== ========================
      2 vCPUs \| 8 GiB   50G
      8 vCPUs \| 32 GiB  50G
      ================== ========================

-  Ascend resources

   .. table:: **Table 3** Capacities of the cache directories for Ascend resources

      ===================== ========================
      Ascend Specifications cache Directory Capacity
      ===================== ========================
      Ascend 910            3T
      ===================== ========================
