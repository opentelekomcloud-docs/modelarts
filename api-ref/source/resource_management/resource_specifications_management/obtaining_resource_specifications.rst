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

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID.
   ========== ========= ====== ===========

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

   +-----------------------+------------------------------------------------------------------------------------------------+----------------------------------------------------+
   | Parameter             | Type                                                                                           | Description                                        |
   +=======================+================================================================================================+====================================================+
   | apiVersion            | String                                                                                         | API version. Options:                              |
   |                       |                                                                                                |                                                    |
   |                       |                                                                                                | -  **v1**                                          |
   +-----------------------+------------------------------------------------------------------------------------------------+----------------------------------------------------+
   | kind                  | String                                                                                         | Resource type. Options:                            |
   |                       |                                                                                                |                                                    |
   |                       |                                                                                                | -  **ResourceFlavorList**: resource specifications |
   +-----------------------+------------------------------------------------------------------------------------------------+----------------------------------------------------+
   | metadata              | :ref:`metadata <en-us_topic_0000002080295913__response_metadata>` object                       | Metadata of resource specifications.               |
   +-----------------------+------------------------------------------------------------------------------------------------+----------------------------------------------------+
   | items                 | Array of :ref:`ResourceFlavor <en-us_topic_0000002080295913__response_resourceflavor>` objects | Resource specifications.                           |
   +-----------------------+------------------------------------------------------------------------------------------------+----------------------------------------------------+

.. _en-us_topic_0000002080295913__response_metadata:

.. table:: **Table 4** metadata

   ================== ======= ========================================
   Parameter          Type    Description
   ================== ======= ========================================
   continue           String  Next query location in pagination query.
   remainingItemCount Integer Remaining resources.
   ================== ======= ========================================

.. _en-us_topic_0000002080295913__response_resourceflavor:

.. table:: **Table 5** ResourceFlavor

   +-----------------------+--------------------------------------------------------------------------------------------------+-----------------------------------------------+
   | Parameter             | Type                                                                                             | Description                                   |
   +=======================+==================================================================================================+===============================================+
   | apiVersion            | String                                                                                           | API version. Options:                         |
   |                       |                                                                                                  |                                               |
   |                       |                                                                                                  | -  **v1**                                     |
   +-----------------------+--------------------------------------------------------------------------------------------------+-----------------------------------------------+
   | kind                  | String                                                                                           | Resource type. Options:                       |
   |                       |                                                                                                  |                                               |
   |                       |                                                                                                  | -  **ResourceFlavor**: resource specification |
   +-----------------------+--------------------------------------------------------------------------------------------------+-----------------------------------------------+
   | metadata              | :ref:`metadata <en-us_topic_0000002080295913__response_metadata>` object                         | Metadata of a resource specification.         |
   +-----------------------+--------------------------------------------------------------------------------------------------+-----------------------------------------------+
   | spec                  | :ref:`ResourceFlavorSpec <en-us_topic_0000002080295913__response_resourceflavorspec>` object     | Description of a resource specification.      |
   +-----------------------+--------------------------------------------------------------------------------------------------+-----------------------------------------------+
   | status                | :ref:`ResourceFlavorStatus <en-us_topic_0000002080295913__response_resourceflavorstatus>` object | Status of a resource specification.           |
   +-----------------------+--------------------------------------------------------------------------------------------------+-----------------------------------------------+

.. table:: **Table 6** metadata

   +-----------+------------------------------------------------------------------------------------------------+------------------------------------+
   | Parameter | Type                                                                                           | Description                        |
   +===========+================================================================================================+====================================+
   | name      | String                                                                                         | Resource specification name.       |
   +-----------+------------------------------------------------------------------------------------------------+------------------------------------+
   | labels    | :ref:`ResourceFlavorLabel <en-us_topic_0000002080295913__response_resourceflavorlabel>` object | Labels of a resource specification |
   +-----------+------------------------------------------------------------------------------------------------+------------------------------------+

.. _en-us_topic_0000002080295913__response_resourceflavorlabel:

.. table:: **Table 7** ResourceFlavorLabel

   +-------------------------------+--------+-----------------------------------------------------------------------+
   | Parameter                     | Type   | Description                                                           |
   +===============================+========+=======================================================================+
   | os.modelarts/scope            | String | Job types supported by a resource specification                       |
   +-------------------------------+--------+-----------------------------------------------------------------------+
   | os.modelarts.flavor/baremetal | String | BMS flavor label. **true** indicates that the flavor is a BMS flavor. |
   +-------------------------------+--------+-----------------------------------------------------------------------+

.. _en-us_topic_0000002080295913__response_resourceflavorspec:

.. table:: **Table 8** ResourceFlavorSpec

   +-----------------------+------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                     | Description                                                                                           |
   +=======================+==========================================================================================+=======================================================================================================+
   | type                  | String                                                                                   | Resource specification type. Options:                                                                 |
   |                       |                                                                                          |                                                                                                       |
   |                       |                                                                                          | -  **Dedicate**: physical resources                                                                   |
   |                       |                                                                                          |                                                                                                       |
   |                       |                                                                                          | -  **Logical**: logical resources                                                                     |
   +-----------------------+------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | cpuArch               | String                                                                                   | Computer architecture. Options:                                                                       |
   |                       |                                                                                          |                                                                                                       |
   |                       |                                                                                          | -  **x86**                                                                                            |
   |                       |                                                                                          |                                                                                                       |
   |                       |                                                                                          | -  **arm64**                                                                                          |
   +-----------------------+------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | cpu                   | String                                                                                   | Number of CPU cores.                                                                                  |
   +-----------------------+------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | memory                | String                                                                                   | Memory size in GiB.                                                                                   |
   +-----------------------+------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | gpu                   | :ref:`gpu <en-us_topic_0000002080295913__response_gpu>` object                           | GPU information.                                                                                      |
   +-----------------------+------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | npu                   | :ref:`npu <en-us_topic_0000002080295913__response_npu>` object                           | NPU information.                                                                                      |
   +-----------------------+------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | dataVolumes           | Array of :ref:`dataVolumes <en-us_topic_0000002080295913__response_datavolumes>` objects | Data disks                                                                                            |
   +-----------------------+------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | billingModes          | Array of integers                                                                        | Billing mode supported by the flavor. The options are as follows:                                     |
   |                       |                                                                                          |                                                                                                       |
   |                       |                                                                                          | -  **0**: pay-per-use                                                                                 |
   +-----------------------+------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | billingCode           | String                                                                                   | Resource flavor code. This parameter corresponds to the offering released on the operations platform. |
   +-----------------------+------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | jobFlavors            | Array of strings                                                                         | Training job types supported by resource specifications.                                              |
   +-----------------------+------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+
   | nodeConfigTemplate    | String                                                                                   | Node configuration template used by resource flavor                                                   |
   +-----------------------+------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002080295913__response_gpu:

.. table:: **Table 9** gpu

   ========= ====== ==============
   Parameter Type   Description
   ========= ====== ==============
   type      String GPU type.
   size      String Number of GPUs
   memory    String GPU memory
   ========= ====== ==============

.. _en-us_topic_0000002080295913__response_npu:

.. table:: **Table 10** npu

   ========= ====== ===============
   Parameter Type   Description
   ========= ====== ===============
   type      String NPU type.
   size      String Number of NPUs.
   memory    String NPU memory
   ========= ====== ===============

.. _en-us_topic_0000002080295913__response_datavolumes:

.. table:: **Table 11** dataVolumes

   +-----------------------+-----------------------+-----------------------------------+
   | Parameter             | Type                  | Description                       |
   +=======================+=======================+===================================+
   | volumeType            | String                | Disk type. Options:               |
   |                       |                       |                                   |
   |                       |                       | -  **SSD**: ultra-high I/O disk   |
   |                       |                       |                                   |
   |                       |                       | -  **GPSSD**: general-purpose SSD |
   |                       |                       |                                   |
   |                       |                       | -  **SAS**: high I/O disk         |
   |                       |                       |                                   |
   |                       |                       | -  **SATA**: common disk          |
   +-----------------------+-----------------------+-----------------------------------+
   | size                  | String                | Disk size, in GiB                 |
   +-----------------------+-----------------------+-----------------------------------+

.. _en-us_topic_0000002080295913__response_resourceflavorstatus:

.. table:: **Table 12** ResourceFlavorStatus

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

.. table:: **Table 13** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 404**

.. table:: **Table 14** Response body parameters

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
       "status" : {
         "phase" : {
           "xxxxxx-7a" : "soldout",
           "xxxxxx-7b" : "soldout",
           "xxxxxx-7c" : "normal"
         }
       }
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
