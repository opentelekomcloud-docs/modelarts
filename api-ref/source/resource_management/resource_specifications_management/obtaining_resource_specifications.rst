:original_name: ListResourceFlavors.html

.. _ListResourceFlavors:

Obtaining Resource Specifications
=================================

Function
--------

Obtain resource specifications.

URI
---

GET /v1/{project_id}/resourceflavors

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                              |
   +============+===========+========+==========================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +---------------+-----------+---------+----------------------------------------------+
   | Parameter     | Mandatory | Type    | Description                                  |
   +===============+===========+=========+==============================================+
   | continue      | No        | String  | Previous query location in pagination query. |
   +---------------+-----------+---------+----------------------------------------------+
   | labelSelector | No        | String  | Filter by label.                             |
   +---------------+-----------+---------+----------------------------------------------+
   | limit         | No        | Integer | Number of records on each page.              |
   +---------------+-----------+---------+----------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------------------+--------------------------------------------------------------------------------------------------------------+----------------------------------------------------+
   | Parameter             | Type                                                                                                         | Description                                        |
   +=======================+==============================================================================================================+====================================================+
   | apiVersion            | String                                                                                                       | API version. Options:                              |
   |                       |                                                                                                              |                                                    |
   |                       |                                                                                                              | -  **v1**                                          |
   +-----------------------+--------------------------------------------------------------------------------------------------------------+----------------------------------------------------+
   | kind                  | String                                                                                                       | Resource type. Options:                            |
   |                       |                                                                                                              |                                                    |
   |                       |                                                                                                              | -  **ResourceFlavorList**: resource specifications |
   +-----------------------+--------------------------------------------------------------------------------------------------------------+----------------------------------------------------+
   | metadata              | :ref:`ResourceFlavorListMetadata <en-us_topic_0000002374856441__response_resourceflavorlistmetadata>` object | Metadata of resource specifications.               |
   +-----------------------+--------------------------------------------------------------------------------------------------------------+----------------------------------------------------+
   | items                 | Array of :ref:`ResourceFlavor <en-us_topic_0000002374856441__response_resourceflavor>` objects               | Resource specifications.                           |
   +-----------------------+--------------------------------------------------------------------------------------------------------------+----------------------------------------------------+

.. _en-us_topic_0000002374856441__response_resourceflavorlistmetadata:

.. table:: **Table 4** ResourceFlavorListMetadata

   ================== ======= ========================================
   Parameter          Type    Description
   ================== ======= ========================================
   continue           String  Next query position in pagination query.
   remainingItemCount Integer Remaining resources.
   ================== ======= ========================================

.. _en-us_topic_0000002374856441__response_resourceflavor:

.. table:: **Table 5** ResourceFlavor

   +-----------------------+------------------------------------------------------------------------------------------------------+-----------------------------------------------+
   | Parameter             | Type                                                                                                 | Description                                   |
   +=======================+======================================================================================================+===============================================+
   | apiVersion            | String                                                                                               | API version. Options:                         |
   |                       |                                                                                                      |                                               |
   |                       |                                                                                                      | -  **v1**                                     |
   +-----------------------+------------------------------------------------------------------------------------------------------+-----------------------------------------------+
   | kind                  | String                                                                                               | Resource type. Options:                       |
   |                       |                                                                                                      |                                               |
   |                       |                                                                                                      | -  **ResourceFlavor**: resource specification |
   +-----------------------+------------------------------------------------------------------------------------------------------+-----------------------------------------------+
   | metadata              | :ref:`ResourceFlavorMetadata <en-us_topic_0000002374856441__response_resourceflavormetadata>` object | Metadata of a resource specification.         |
   +-----------------------+------------------------------------------------------------------------------------------------------+-----------------------------------------------+
   | spec                  | :ref:`ResourceFlavorSpec <en-us_topic_0000002374856441__response_resourceflavorspec>` object         | Description of a resource specification.      |
   +-----------------------+------------------------------------------------------------------------------------------------------+-----------------------------------------------+
   | status                | :ref:`ResourceFlavorStatus <en-us_topic_0000002374856441__response_resourceflavorstatus>` object     | Status of a resource specification.           |
   +-----------------------+------------------------------------------------------------------------------------------------------+-----------------------------------------------+

.. _en-us_topic_0000002374856441__response_resourceflavormetadata:

.. table:: **Table 6** ResourceFlavorMetadata

   +-------------+------------------------------------------------------------------------------------------------------------+-----------------------------------+
   | Parameter   | Type                                                                                                       | Description                       |
   +=============+============================================================================================================+===================================+
   | name        | String                                                                                                     | Resource flavor name.             |
   +-------------+------------------------------------------------------------------------------------------------------------+-----------------------------------+
   | labels      | :ref:`ResourceFlavorLabel <en-us_topic_0000002374856441__response_resourceflavorlabel>` object             | Labels of a resource flavor.      |
   +-------------+------------------------------------------------------------------------------------------------------------+-----------------------------------+
   | annotations | :ref:`ResourceFlavorAnnotations <en-us_topic_0000002374856441__response_resourceflavorannotations>` object | Annotations of a resource flavor. |
   +-------------+------------------------------------------------------------------------------------------------------------+-----------------------------------+

.. _en-us_topic_0000002374856441__response_resourceflavorlabel:

.. table:: **Table 7** ResourceFlavorLabel

   +-------------------------------+--------+---------------------------------------------------------------------------------------------+
   | Parameter                     | Type   | Description                                                                                 |
   +===============================+========+=============================================================================================+
   | os.modelarts/scope            | String | Job types supported by a resource specification                                             |
   +-------------------------------+--------+---------------------------------------------------------------------------------------------+
   | os.modelarts.flavor/baremetal | String | BMS flavor label. **true** indicates that the flavor is a BMS flavor.                       |
   +-------------------------------+--------+---------------------------------------------------------------------------------------------+
   | os.modelarts.flavor/localdisk | String | Whether a local disk is contained. **true** indicates that the flavor contains local disks. |
   +-------------------------------+--------+---------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002374856441__response_resourceflavorannotations:

.. table:: **Table 8** ResourceFlavorAnnotations

   +--------------------------------------------+--------+------------------------------------------------------------------+
   | Parameter                                  | Type   | Description                                                      |
   +============================================+========+==================================================================+
   | os.modelarts.resourceflavor/volume.configs | String | Constraints on additional disks attached to the resource flavor. |
   +--------------------------------------------+--------+------------------------------------------------------------------+

.. _en-us_topic_0000002374856441__response_resourceflavorspec:

.. table:: **Table 9** ResourceFlavorSpec

   +-----------------------+------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
   | Parameter             | Type                                                                                                       | Description                                                       |
   +=======================+============================================================================================================+===================================================================+
   | type                  | String                                                                                                     | Resource specification type.                                      |
   +-----------------------+------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
   | cpuArch               | String                                                                                                     | Computer architecture. Options:                                   |
   |                       |                                                                                                            |                                                                   |
   |                       |                                                                                                            | -  **x86**                                                        |
   |                       |                                                                                                            |                                                                   |
   |                       |                                                                                                            | -  **arm64**                                                      |
   +-----------------------+------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
   | cpu                   | String                                                                                                     | Number of CPU cores.                                              |
   +-----------------------+------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
   | memory                | String                                                                                                     | Memory size in GiB.                                               |
   +-----------------------+------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
   | gpu                   | :ref:`ResourceFlavorXpu <en-us_topic_0000002374856441__response_resourceflavorxpu>` object                 | GPU information.                                                  |
   +-----------------------+------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
   | npu                   | :ref:`ResourceFlavorXpu <en-us_topic_0000002374856441__response_resourceflavorxpu>` object                 | NPU information.                                                  |
   +-----------------------+------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
   | dataVolumes           | Array of :ref:`DataVolumeItem <en-us_topic_0000002374856441__response_datavolumeitem>` objects             | Data disks                                                        |
   +-----------------------+------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
   | rootVolume            | :ref:`RootVolume <en-us_topic_0000002374856441__response_rootvolume>` object                               | System disk information.                                          |
   +-----------------------+------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
   | jobFlavors            | Array of strings                                                                                           | Training job types supported by resource specifications.          |
   +-----------------------+------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
   | nodeConfigTemplate    | String                                                                                                     | Node configuration template used by resource flavor               |
   +-----------------------+------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
   | creatingSteps         | Array of :ref:`FlavorCreatingStepVO <en-us_topic_0000002374856441__response_flavorcreatingstepvo>` objects | Information about the resource flavor for creating nodes by step. |
   +-----------------------+------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
   | flavorBootType        | String                                                                                                     | Boot type of a BMS. The options are as follows:                   |
   |                       |                                                                                                            |                                                                   |
   |                       |                                                                                                            | -  **LocalDisk**: local disk                                      |
   |                       |                                                                                                            |                                                                   |
   |                       |                                                                                                            | -  **Volume**: cloud hard disk (quick provisioning)               |
   +-----------------------+------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------+
   | localDiskDetail       | String                                                                                                     | Physical disk specifications.                                     |
   +-----------------------+------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------+

.. _en-us_topic_0000002374856441__response_resourceflavorxpu:

.. table:: **Table 10** ResourceFlavorXpu

   ========= ====== ===============
   Parameter Type   Description
   ========= ====== ===============
   type      String XPU type.
   size      String Number of XPUs.
   memory    String XPU memory.
   ========= ====== ===============

.. _en-us_topic_0000002374856441__response_datavolumeitem:

.. table:: **Table 11** DataVolumeItem

   +-----------------------+-----------------------+----------------------------------------+
   | Parameter             | Type                  | Description                            |
   +=======================+=======================+========================================+
   | volumeType            | String                | Disk type. The options are as follows: |
   |                       |                       |                                        |
   |                       |                       | -  **SSD**: ultra-high I/O disk        |
   |                       |                       |                                        |
   |                       |                       | -  **GPSSD**: general-purpose SSD      |
   |                       |                       |                                        |
   |                       |                       | -  **SAS**: high I/O disk              |
   |                       |                       |                                        |
   |                       |                       | -  **SATA**: common disk               |
   +-----------------------+-----------------------+----------------------------------------+
   | size                  | String                | Disk size, in GiB.                     |
   +-----------------------+-----------------------+----------------------------------------+

.. _en-us_topic_0000002374856441__response_rootvolume:

.. table:: **Table 12** RootVolume

   +-----------------------+-----------------------+----------------------------------------+
   | Parameter             | Type                  | Description                            |
   +=======================+=======================+========================================+
   | volumeType            | String                | Disk type. The options are as follows: |
   |                       |                       |                                        |
   |                       |                       | -  **SSD**: ultra-high I/O disk        |
   |                       |                       |                                        |
   |                       |                       | -  **GPSSD**: general-purpose SSD      |
   |                       |                       |                                        |
   |                       |                       | -  **SAS**: high I/O disk              |
   |                       |                       |                                        |
   |                       |                       | -  **SATA**: common disk               |
   +-----------------------+-----------------------+----------------------------------------+
   | size                  | String                | Disk size, in GiB.                     |
   +-----------------------+-----------------------+----------------------------------------+

.. _en-us_topic_0000002374856441__response_flavorcreatingstepvo:

.. table:: **Table 13** FlavorCreatingStepVO

   +-------------+--------------------------------------------------------------------------------+----------------------------------------+
   | Parameter   | Type                                                                           | Description                            |
   +=============+================================================================================+========================================+
   | displayInfo | :ref:`DisplayInfo <en-us_topic_0000002374856441__response_displayinfo>` object | Name of the step displayed externally. |
   +-------------+--------------------------------------------------------------------------------+----------------------------------------+
   | step        | Integer                                                                        | Step.                                  |
   +-------------+--------------------------------------------------------------------------------+----------------------------------------+
   | type        | String                                                                         | Batch type.                            |
   +-------------+--------------------------------------------------------------------------------+----------------------------------------+

.. _en-us_topic_0000002374856441__response_displayinfo:

.. table:: **Table 14** DisplayInfo

   ========= ====== =============
   Parameter Type   Description
   ========= ====== =============
   en_US     String English name.
   ========= ====== =============

.. _en-us_topic_0000002374856441__response_resourceflavorstatus:

.. table:: **Table 15** ResourceFlavorStatus

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                             |
   +=======================+=======================+=========================================================================================================+
   | phase                 | Map<String,String>    | Sales status of a resource specification in each AZ. The value is (AZ, Status). Options for **Status**: |
   |                       |                       |                                                                                                         |
   |                       |                       | -  **normal**: The specification is on-sales.                                                           |
   |                       |                       |                                                                                                         |
   |                       |                       | -  **soldout**: The specification is sold out.                                                          |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+

**Status code: 401**

.. table:: **Table 16** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 404**

.. table:: **Table 17** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

This API is used to obtain resource specifications.

.. code-block:: text

   GET https://{endpoint}/v1/{project_id}/resourceflavors

   { }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "kind" : "ResourceFlavorList",
     "apiVersion" : "v1",
     "metadata" : { },
     "items" : [ {
       "kind" : "ResourceFlavor",
       "apiVersion" : "v1",
       "metadata" : {
         "name" : "modelarts.vm.cpu8u32g",
         "labels" : { }
       },
       "spec" : {
         "cpuArch" : "x86",
         "cpu" : "8",
         "memory" : "32Gi",
         "type" : "Dedicate",
         "billingModes" : [ 0 ],
         "dataVolumes" : [ {
           "volumeType" : "SSD",
           "size" : "500Gi"
         } ]
       },
     } ]
   }

**Status code: 401**

Authorization failed.

.. code-block::

   {
     "error_code" : "ModelArts.50001000",
     "error_msg" : "token is invalid"
   }

**Status code: 404**

Not found.

.. code-block::

   {
     "error_code" : "ModelArts.50005101",
     "error_msg" : "Resourceflavor not found."
   }

Status Codes
------------

=========== =====================
Status Code Description
=========== =====================
200         OK
401         Authorization failed.
404         Not found.
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
