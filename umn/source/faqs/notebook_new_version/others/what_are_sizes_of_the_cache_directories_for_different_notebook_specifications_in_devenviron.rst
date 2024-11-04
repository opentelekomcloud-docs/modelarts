:original_name: modelarts_05_3151.html

.. _modelarts_05_3151:

What Are Sizes of the /cache Directories for Different Notebook Specifications in DevEnviron?
=============================================================================================

When creating a notebook instance, you can select CPUs, GPUs, or Ascend based on the data volume.

ModelArts mounts disks to **/cache**. You can use this directory to store temporary files. The **/cache** directory shares resources with the code directory. The directory size varies depending on resource specifications.

No disks can be mounted to **/cache** for CPUs. When only one GPU or Ascend card is used, the **/cache** directory size is limited to 500 GB. If multiple GPUs or Ascend cards are used, the **/cache** directory size is limited to 3 TB and calculated using the following formula: **/cache** directory size = Number of cards x 500 GB. For details, see :ref:`Table 1 <en-us_topic_0000002079104857__table8250191216198>`.

.. _en-us_topic_0000002079104857__table8250191216198:

.. table:: **Table 1** /cache directory sizes for different notebook specifications

   =================== =====================
   Specification       /cache Directory Size
   GPU, 0.25 cards     500 GB x 0.25
   GPU, 0.5 cards      500 GB x 0.5
   GPU, 1 card         500 GB
   GPU, dual cards     500 GB x 2
   GPU, four cards     500 GB x 4
   GPU, eight cards    3 TB
   Ascend, single card 500 GB
   Ascend, dual cards  500 GB x 2
   Ascend, four cards  500 GB x 4
   Ascend, eight cards 3 TB
   CPU                 N/A
   =================== =====================
