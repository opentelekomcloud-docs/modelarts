:original_name: modelarts_23_0217.html

.. _modelarts_23_0217:

Specifications for Custom Images Used for Training Jobs
=======================================================

When creating an image using locally developed models and training scripts, ensure that they meet the specifications defined by ModelArts.

Specifications
--------------

-  Custom images cannot contain malicious code.
-  Part of content in the basic images cannot be changed, including all the files in **/bin**, **/sbin**, **/usr**, and **/lib(64)**, some important configuration files in **/etc**, and the ModelArts tools in **$HOME**.
-  A file cannot be added whose owner is **root** and has permission **setuid** or **setgid**.
-  The size of a custom image cannot exceed 9.5 GB.

-  To ensure that the log content can be displayed normally, the logs must be standard output.
-  The default user of a custom image must be the user whose UID is **1101**.
-  Custom images can be developed based on basic ModelArts images. For details about the supported basic images, see :ref:`Overview of a Basic Image Package <modelarts_23_0217__en-us_topic_0212179951_section1126616610513>`.

.. _modelarts_23_0217__en-us_topic_0212179951_section1126616610513:

Overview of a Basic Image Package
---------------------------------

To facilitate code download, training log output, and log file upload to OBS, ModelArts provides basic image packages for creating custom images. The basic images provided by ModelArts have the following features:

-  Some necessary tools are available in the basic image. You need to create a custom image based on the basic images provided by ModelArts.
-  ModelArts continuously updates the basic image versions. For compatible updates, after the basic images are updated, you can still use the old images. For incompatible updates, the custom images created based on the old version cannot run on ModelArts, but the approved custom images can still be used.
-  If a custom image fails to be approved and the audit log contains an error message indicating that the basic image does not match, you need to use a new basic image to create an image.

Run the following command to obtain a ModelArts image:

.. code-block::

   docker pull <Address for obtaining a basic image>

After customizing an image, upload it to SWR. Make sure that you have created an organization and obtained the password for logging in to SWR. For details, see .

.. code-block::

   docker push  swr.<region>.xxx.com/<Organization to which the target image belongs>/<Image name>

Obtain basic images based on chip requirements:

CPU-based Basic Images
----------------------

Address for obtaining a basic image

.. code-block::

   swr.<region>.xxx.com/modelarts-job-dev-image/custom-cpu-base:1.3

.. table:: **Table 1** Optional parameters

   ========= ============== ===============================
   Parameter Optional Value Description
   ========= ============== ===============================
   <region>  eu-de          Region where the image resides.
   ========= ============== ===============================

:ref:`Table 2 <modelarts_23_0217__en-us_topic_0212179951_table42317014714>` and :ref:`Table 3 <modelarts_23_0217__en-us_topic_0212179951_table624501372>` list the components and tools used by basic images.

.. _modelarts_23_0217__en-us_topic_0212179951_table42317014714:

.. table:: **Table 2** Components

   +--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Component    | Description                                                                                                                                                                       |
   +==============+===================================================================================================================================================================================+
   | run_train.sh | Training boot script. You can download the code directory, run training commands, redirect training log output, and upload log files to OBS after training commands are executed. |
   +--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _modelarts_23_0217__en-us_topic_0212179951_table624501372:

.. table:: **Table 3** Tool list

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

GPU-based Basic Images
----------------------

-  Image of the CUDA 10.0, 10.1, or 10.2 version, using Ubuntu 18.04 as the basic image and with MoXing pre-installed by default

   .. code-block::

      swr.<region>.xxx.com/modelarts-job-dev-image/custom-base-<cuda version>-<python version>-<os>-<arch>:<image tag>

-  Image of the CUDA 8, 9, or 92 version, with MoXing pre-installed by default

   .. code-block::

      swr.<region>.xxx.com/modelarts-job-dev-image/custom-gpu-<cuda version>-inner-moxing-<python version>:<image tag>

-  Image of the CUDA 8, 9, or 92 version

   .. code-block::

      swr.<region>.xxx.com/modelarts-job-dev-image/custom-gpu-<cuda version>-base:<image tag>

   .. table:: **Table 4** Optional parameters

      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Possible Value        | Description                                                                                                         |
      +=======================+=======================+=====================================================================================================================+
      | <region>              | eu-de                 | Region where the image resides.                                                                                     |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------+
      | <cuda version>        | -  cuda92             | CUDA version installed in the image                                                                                 |
      |                       | -  cuda9              |                                                                                                                     |
      |                       | -  cuda8              | .. note::                                                                                                           |
      |                       | -  cuda10.0           |                                                                                                                     |
      |                       | -  cuda10.1           |    Check the CUDA version. After the version is specified, it cannot be changed. Otherwise, the training will fail. |
      |                       | -  cuda10.2           |                                                                                                                     |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------+
      | <image tag>           | -  1.1                | Image version                                                                                                       |
      |                       | -  1.3                |                                                                                                                     |
      |                       |                       | -  Version 1.3 available for CUDA 8, 9, or 92 version                                                               |
      |                       |                       | -  Version 1.1 available for CUDA 10.0, 10.1, or 10.2 version                                                       |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------+
      | python version        | -  cp27               | Python environment                                                                                                  |
      |                       | -  cp36               |                                                                                                                     |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------+
      | os                    | ubuntu18.04           | Operating system                                                                                                    |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------+
      | arch                  | x86                   | Architecture                                                                                                        |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------+

:ref:`Table 2 <modelarts_23_0217__en-us_topic_0212179951_table42317014714>` and :ref:`Table 3 <modelarts_23_0217__en-us_topic_0212179951_table624501372>` list the components and tools used by basic images.

.. table:: **Table 5** Components

   +--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Component    | Description                                                                                                                                                                       |
   +==============+===================================================================================================================================================================================+
   | run_train.sh | Training boot script. You can download the code directory, run training commands, redirect training log output, and upload log files to OBS after training commands are executed. |
   +--------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 6** Tool list

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
