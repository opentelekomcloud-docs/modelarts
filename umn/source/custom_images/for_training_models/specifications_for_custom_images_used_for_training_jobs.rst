:original_name: modelarts_23_0217.html

.. _modelarts_23_0217:

Specifications for Custom Images Used for Training Jobs
=======================================================

When creating an image using locally developed models and training scripts, ensure that they meet the specifications defined by ModelArts.

Specifications
--------------

-  Custom images cannot contain malicious code.
-  Part of content in the base images cannot be changed, including all the files in **/bin**, **/sbin**, **/usr**, and **/lib(64)**, some important configuration files in **/etc**, and the ModelArts tools in **$HOME**.
-  A file cannot be added whose owner is **root** and has permission **setuid** or **setgid**.
-  The size of a custom image cannot exceed 9.5 GB.

-  To ensure that the log content can be displayed properly, the logs must be standard output.
-  The default user of a custom image must be the user whose UID is **1101**.
-  Custom images can be developed based on basic ModelArts images. For details about the supported base images, see :ref:`Overview of a Base Image Package <modelarts_23_0217__en-us_topic_0212179951_section1126616610513>`.

.. _modelarts_23_0217__en-us_topic_0212179951_section1126616610513:

Overview of a Base Image Package
--------------------------------

To facilitate code download, training log output, and log file upload to OBS, ModelArts provides base image packages for creating custom images. The base images provided by ModelArts have the following features:

-  Some necessary tools are available in the base image. Create a custom image based on the base images provided by ModelArts.
-  ModelArts continuously updates the base image versions. For compatible updates, after the base images are updated, you can still use the old images. For incompatible updates, the custom images created based on the old version cannot run on ModelArts, but the approved custom images can still be used.
-  If a custom image fails to be approved and the audit log contains an error message indicating that the base image does not match, use a new base image to create an image.

Run the following command to obtain a ModelArts image:

.. code-block::

   docker pull <Address for obtaining a base image>

After customizing an image, upload it to SWR. Make sure that you have created an organization and obtained the password for logging in to SWR. For details, see .

.. code-block::

   docker push  swr.<region>.xxx.com/<Organization to which the target image belongs>/<Image name>

Obtain base images based on chip requirements:

CPU-based Base Images
---------------------

Address for obtaining a base image

.. code-block::

   swr.<region>.xxx.com/modelarts-job-dev-image/custom-cpu-base:1.3

.. table:: **Table 1** Optional parameters

   ========= ============== ===============================
   Parameter Optional Value Description
   ========= ============== ===============================
   <region>  eu-de          Region where the image resides.
   ========= ============== ===============================

:ref:`Table 2 <modelarts_23_0217__en-us_topic_0212179951_table42317014714>` and :ref:`Table 3 <modelarts_23_0217__en-us_topic_0212179951_table624501372>` list the components and tools used by base images.

.. _modelarts_23_0217__en-us_topic_0212179951_table42317014714:

.. table:: **Table 2** Components

   +--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Component    | Description                                                                                                                                                                       |
   +==============+===================================================================================================================================================================================+
   | run_train.sh | Training boot script. You can download the code directory, run training commands, redirect training log output, and upload log files to OBS after training commands are executed. |
   +--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _modelarts_23_0217__en-us_topic_0212179951_table624501372:

.. table:: **Table 3** Tools

   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Tool                              | Description                                                                                                                                              |
   +===================================+==========================================================================================================================================================+
   | utils.sh                          | Tool script. The **run_train.sh** script depends on this script.                                                                                         |
   |                                   |                                                                                                                                                          |
   |                                   | It provides methods such as SK decryption, code directory download, and log file upload.                                                                 |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ip_mapper.py                      | Script for obtaining NIC addresses.                                                                                                                      |
   |                                   |                                                                                                                                                          |
   |                                   | By default, the IP address of the **ib0** NIC is obtained. Training code can use the IP address of the **ib0** NIC to accelerate network communications. |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dls-downloader.py                 | OBS download script. The **utils.sh** script depends on this script.                                                                                     |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+

GPU-based Base Images
---------------------

-  Image of the CUDA 9 version

   .. code-block::

      swr.<region>.xxx.com/modelarts-job-dev-image/custom-gpu-<cuda version>-base:<image tag>

   .. table:: **Table 4** Optional parameters

      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Possible Value        | Description                                                                                                         |
      +=======================+=======================+=====================================================================================================================+
      | <region>              | eu-de                 | Region where the image resides.                                                                                     |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------+
      | <cuda version>        | -  cuda9              | CUDA version installed in the image                                                                                 |
      |                       |                       |                                                                                                                     |
      |                       |                       | .. note::                                                                                                           |
      |                       |                       |                                                                                                                     |
      |                       |                       |    Check the CUDA version. After the version is specified, it cannot be changed. Otherwise, the training will fail. |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------+
      | <image tag>           | -  1.3                | Image version                                                                                                       |
      |                       |                       |                                                                                                                     |
      |                       |                       | -  Version 1.3 available for CUDA 9                                                                                 |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------+
      | python version        | -  cp36               | Python environment                                                                                                  |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------+
      | os                    | ubuntu18.04           | Operating system                                                                                                    |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------+
      | arch                  | x86                   | Architecture                                                                                                        |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------+

:ref:`Table 2 <modelarts_23_0217__en-us_topic_0212179951_table42317014714>` and :ref:`Table 3 <modelarts_23_0217__en-us_topic_0212179951_table624501372>` list the components and tools used by base images.

.. table:: **Table 5** Components

   +--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Component    | Description                                                                                                                                                                       |
   +==============+===================================================================================================================================================================================+
   | run_train.sh | Training boot script. You can download the code directory, run training commands, redirect training log output, and upload log files to OBS after training commands are executed. |
   +--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 6** Tools

   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Tool                              | Description                                                                                                                                              |
   +===================================+==========================================================================================================================================================+
   | utils.sh                          | Tool script. The **run_train.sh** script depends on this script.                                                                                         |
   |                                   |                                                                                                                                                          |
   |                                   | It provides methods such as SK decryption, code directory download, and log file upload.                                                                 |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ip_mapper.py                      | Script for obtaining NIC addresses.                                                                                                                      |
   |                                   |                                                                                                                                                          |
   |                                   | By default, the IP address of the **ib0** NIC is obtained. Training code can use the IP address of the **ib0** NIC to accelerate network communications. |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dls-downloader.py                 | OBS download script. The **utils.sh** script depends on this script.                                                                                     |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
