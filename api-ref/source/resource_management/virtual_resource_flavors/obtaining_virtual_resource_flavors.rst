:original_name: ListVirtualresourceFlavors.html

.. _ListVirtualresourceFlavors:

Obtaining Virtual Resource Flavors
==================================

Function
--------

This API is used to obtain virtual resource flavors.

URI
---

GET /v1/{project_id}/virtualresourceflavors

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                              |
   +============+===========+========+==========================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   +-----------------------+--------------------------------------------------------------------------------------------------------------+---------------------------------------------+
   | Parameter             | Type                                                                                                         | Description                                 |
   +=======================+==============================================================================================================+=============================================+
   | apiVersion            | String                                                                                                       | API version. The options are as follows:    |
   |                       |                                                                                                              |                                             |
   |                       |                                                                                                              | -  **v1**                                   |
   +-----------------------+--------------------------------------------------------------------------------------------------------------+---------------------------------------------+
   | kind                  | String                                                                                                       | Resource type. The options are as follows:  |
   |                       |                                                                                                              |                                             |
   |                       |                                                                                                              | -  **ResourceFlavorList**: resource flavors |
   +-----------------------+--------------------------------------------------------------------------------------------------------------+---------------------------------------------+
   | metadata              | :ref:`ResourceFlavorListMetadata <en-us_topic_0000002374856425__response_resourceflavorlistmetadata>` object | Metadata of resource flavors.               |
   +-----------------------+--------------------------------------------------------------------------------------------------------------+---------------------------------------------+
   | items                 | Array of :ref:`ResourceFlavor <en-us_topic_0000002374856425__response_resourceflavor>` objects               | Resource flavors.                           |
   +-----------------------+--------------------------------------------------------------------------------------------------------------+---------------------------------------------+

.. _en-us_topic_0000002374856425__response_resourceflavorlistmetadata:

.. table:: **Table 3** ResourceFlavorListMetadata

   ================== ======= ========================================
   Parameter          Type    Description
   ================== ======= ========================================
   continue           String  Next query position in pagination query.
   remainingItemCount Integer Remaining resources.
   ================== ======= ========================================

.. _en-us_topic_0000002374856425__response_resourceflavor:

.. table:: **Table 4** ResourceFlavor

   +-----------------------+------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | Parameter             | Type                                                                                                 | Description                                |
   +=======================+======================================================================================================+============================================+
   | apiVersion            | String                                                                                               | API version. The options are as follows:   |
   |                       |                                                                                                      |                                            |
   |                       |                                                                                                      | -  **v1**                                  |
   +-----------------------+------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | kind                  | String                                                                                               | Resource type. The options are as follows: |
   |                       |                                                                                                      |                                            |
   |                       |                                                                                                      | -  **ResourceFlavor**: resource flavor     |
   +-----------------------+------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | metadata              | :ref:`ResourceFlavorMetadata <en-us_topic_0000002374856425__response_resourceflavormetadata>` object | Metadata of a resource flavor.             |
   +-----------------------+------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | spec                  | :ref:`ResourceFlavorSpec <en-us_topic_0000002374856425__response_resourceflavorspec>` object         | Description of a resource flavor.          |
   +-----------------------+------------------------------------------------------------------------------------------------------+--------------------------------------------+

.. _en-us_topic_0000002374856425__response_resourceflavormetadata:

.. table:: **Table 5** ResourceFlavorMetadata

   ========= ====== =====================
   Parameter Type   Description
   ========= ====== =====================
   name      String Resource flavor name.
   ========= ====== =====================

.. _en-us_topic_0000002374856425__response_resourceflavorspec:

.. table:: **Table 6** ResourceFlavorSpec

   +-----------------------------+--------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
   | Parameter                   | Type                                                                                       | Description                                                                     |
   +=============================+============================================================================================+=================================================================================+
   | type                        | String                                                                                     | Virtual resource flavor type. The options are as follows:                       |
   |                             |                                                                                            |                                                                                 |
   |                             |                                                                                            | -  **Logical**: logical resources                                               |
   +-----------------------------+--------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
   | cpuArch                     | String                                                                                     | Computer architecture. The options are as follows:                              |
   |                             |                                                                                            |                                                                                 |
   |                             |                                                                                            | -  **x86**                                                                      |
   |                             |                                                                                            |                                                                                 |
   |                             |                                                                                            | -  **arm64**                                                                    |
   +-----------------------------+--------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
   | cpu                         | String                                                                                     | Number of CPU cores.                                                            |
   +-----------------------------+--------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
   | memory                      | String                                                                                     | Memory size in GiB.                                                             |
   +-----------------------------+--------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
   | npu                         | :ref:`ResourceFlavorXpu <en-us_topic_0000002374856425__response_resourceflavorxpu>` object | Virtual NPU information.                                                        |
   +-----------------------------+--------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
   | virtualResourceTemplateName | String                                                                                     | Template name of the virtual NPU resource corresponding to the resource flavor. |
   +-----------------------------+--------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+

.. _en-us_topic_0000002374856425__response_resourceflavorxpu:

.. table:: **Table 7** ResourceFlavorXpu

   +-------------+--------+------------------------------------------------------------------------------------------+
   | Parameter   | Type   | Description                                                                              |
   +=============+========+==========================================================================================+
   | type        | String | Virtual NPU allocation type, which corresponds to the queried virtual resource template. |
   +-------------+--------+------------------------------------------------------------------------------------------+
   | size        | String | Size. The value is **1**.                                                                |
   +-------------+--------+------------------------------------------------------------------------------------------+
   | resourceKey | String | Resource key for virtual NPU allocation                                                  |
   +-------------+--------+------------------------------------------------------------------------------------------+

**Status code: 404**

.. table:: **Table 8** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Obtain virtual NPU allocation resource flavors.

.. code-block:: text

   GET https://{endpoint}/v1/{project_id}/virtualresourceflavors

Example Responses
-----------------

**Status code: 200**

OK.

.. code-block::

   {
     "kind" : "ResourceFlavorList",
     "apiVersion" : "v1",
     "metadata" : { },
     "items" : [ {
       "kind" : "ResourceFlavor",
       "apiVersion" : "v1",
       "metadata" : {
         "name" : "snt9-280t-vir10-3c-16g",
         "labels" : { }
       },
       "spec" : {
         "cpuArch" : "arm64",
         "cpu" : "8",
         "memory" : "32Gi",
         "type" : "Logical",
         "virtualResourceTemplateName" : "snt9-280t",
         "visibility" : "invisible"
       }
     } ]
   }

**Status code: 404**

Not found.

.. code-block::

   {
     "error_code" : "ModelArts.50005101",
     "error_msg" : "VirtualResourceTemplate {name} not found."
   }

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
200         OK.
404         Not found.
=========== ===========

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
