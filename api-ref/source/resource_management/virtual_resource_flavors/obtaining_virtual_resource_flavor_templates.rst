:original_name: ShowVirtualResourceTemplate.html

.. _ShowVirtualResourceTemplate:

Obtaining Virtual Resource Flavor Templates
===========================================

Function
--------

This API is used to obtain details about a specified virtual resource allocation template.

URI
---

GET /v1/{project_id}/virtualresourcetemplates/{virtualresourcetemplate_name}

.. table:: **Table 1** Path Parameters

   +------------------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                    | Mandatory | Type   | Description                                                                                                                                                                                            |
   +==============================+===========+========+========================================================================================================================================================================================================+
   | project_id                   | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`.                                                                                                               |
   +------------------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | virtualresourcetemplate_name | Yes       | String | Name of the virtual resource allocation template, which corresponds to the **virtualResourceTemplateName** field in the **spec** of the resource flavor obtained using **ListVirtualresourceFlavors**. |
   +------------------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   +-----------------------+------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------+
   | Parameter             | Type                                                                                                                   | Description                                                 |
   +=======================+========================================================================================================================+=============================================================+
   | apiVersion            | String                                                                                                                 | API version. The options are as follows:                    |
   |                       |                                                                                                                        |                                                             |
   |                       |                                                                                                                        | -  **v1**                                                   |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------+
   | kind                  | String                                                                                                                 | Resource type. The options are as follows:                  |
   |                       |                                                                                                                        |                                                             |
   |                       |                                                                                                                        | -  **VirtualResourceTemplate**                              |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------+
   | metadata              | :ref:`VirtualResourceTemplateMetadata <en-us_topic_0000002374896577__response_virtualresourcetemplatemetadata>` object | Metadata of the virtual resource allocation template.       |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------+
   | spec                  | :ref:`VirtualResourceTemplateSpec <en-us_topic_0000002374896577__response_virtualresourcetemplatespec>` object         | Specifications of the virtual resource allocation template. |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------+

.. _en-us_topic_0000002374896577__response_virtualresourcetemplatemetadata:

.. table:: **Table 3** VirtualResourceTemplateMetadata

   ========= ====== =====================================================
   Parameter Type   Description
   ========= ====== =====================================================
   name      String Name of the virtual NPU resource allocation template.
   ========= ====== =====================================================

.. _en-us_topic_0000002374896577__response_virtualresourcetemplatespec:

.. table:: **Table 4** VirtualResourceTemplateSpec

   +------------------+--------------------------------------------------------------------------------------------------+----------------------------------------------+
   | Parameter        | Type                                                                                             | Description                                  |
   +==================+==================================================================================================+==============================================+
   | resources        | String                                                                                           | Physical resource information of the flavor. |
   +------------------+--------------------------------------------------------------------------------------------------+----------------------------------------------+
   | resourceKey      | String                                                                                           | Resource key of the NPU.                     |
   +------------------+--------------------------------------------------------------------------------------------------+----------------------------------------------+
   | virtualResources | Array of :ref:`VitrualResource <en-us_topic_0000002374896577__response_vitrualresource>` objects | Virtual resource list.                       |
   +------------------+--------------------------------------------------------------------------------------------------+----------------------------------------------+

.. _en-us_topic_0000002374896577__response_vitrualresource:

.. table:: **Table 5** VitrualResource

   +-------------+--------------------+------------------------------------------------+
   | Parameter   | Type               | Description                                    |
   +=============+====================+================================================+
   | name        | String             | Name of the virtual resource template.         |
   +-------------+--------------------+------------------------------------------------+
   | resources   | Map<String,String> | Resources used by the virtualization template. |
   +-------------+--------------------+------------------------------------------------+
   | resourceKey | String             | Resource key of the virtualization template.   |
   +-------------+--------------------+------------------------------------------------+

**Status code: 404**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Obtain details about a virtual resource template.

.. code-block:: text

   GET https://{endpoint}/v1/{project_id}/virtualresourcetemplates/{virtualresourcetemplate_name}

Example Responses
-----------------

**Status code: 200**

OK.

.. code-block::

   {
     "apiVersion" : "v1",
     "kind" : "VirtualResourceTemplate",
     "metadata" : {
       "name" : "snt9-280t"
     },
     "spec" : {
       "resources" : {
         "AICORE" : 10,
         "AICPU" : 5,
         "memory" : "32G"
       }
     },
     "virtualResources" : [ {
       "name" : "vir5_1c_8g",
       "resources" : {
         "AICORE" : 5,
         "AICPU" : 1,
         "memory" : "8G"
       },
       "resourceKey" : "npu.accelerator/snt9-5c.1cpu.8g"
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
