:original_name: ShowPluginTemplate.html

.. _ShowPluginTemplate:

Querying a Plug-in Template
===========================

Function
--------

This API is used to obtain details of a specified plug-in template.

URI
---

GET /v1/{project_id}/plugintemplates/{plugintemplate_name}

.. table:: **Table 1** Path Parameters

   +---------------------+-----------------+-----------------+------------------------------------------------------------------------------------------+
   | Parameter           | Mandatory       | Type            | Description                                                                              |
   +=====================+=================+=================+==========================================================================================+
   | project_id          | Yes             | String          | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +---------------------+-----------------+-----------------+------------------------------------------------------------------------------------------+
   | plugintemplate_name | Yes             | String          | Plug-in template name. Options:                                                          |
   |                     |                 |                 |                                                                                          |
   |                     |                 |                 | -  **gpu-driver**: GPU driver plug-in template                                           |
   |                     |                 |                 |                                                                                          |
   |                     |                 |                 | -  **npu-driver**: NPU driver plug-in template                                           |
   +---------------------+-----------------+-----------------+------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   +-----------------------+------------------------------------------------------------------------------------------------------+-----------------------------------------+
   | Parameter             | Type                                                                                                 | Description                             |
   +=======================+======================================================================================================+=========================================+
   | apiVersion            | String                                                                                               | API version. Options:                   |
   |                       |                                                                                                      |                                         |
   |                       |                                                                                                      | -  **v1**                               |
   +-----------------------+------------------------------------------------------------------------------------------------------+-----------------------------------------+
   | kind                  | String                                                                                               | Resource type. Options:                 |
   |                       |                                                                                                      |                                         |
   |                       |                                                                                                      | -  **PluginTemplate**: plug-in template |
   +-----------------------+------------------------------------------------------------------------------------------------------+-----------------------------------------+
   | metadata              | :ref:`PluginTemplateMetadata <en-us_topic_0000002044058268__response_plugintemplatemetadata>` object | Plug-in template metadata               |
   +-----------------------+------------------------------------------------------------------------------------------------------+-----------------------------------------+
   | spec                  | :ref:`PluginTemplateSpec <en-us_topic_0000002044058268__response_plugintemplatespec>` object         | Plug-in template specifications         |
   +-----------------------+------------------------------------------------------------------------------------------------------+-----------------------------------------+

.. _en-us_topic_0000002044058268__response_plugintemplatemetadata:

.. table:: **Table 3** PluginTemplateMetadata

   ========= ====== =====================
   Parameter Type   Description
   ========= ====== =====================
   name      String Plug-in template name
   ========= ====== =====================

.. _en-us_topic_0000002044058268__response_plugintemplatespec:

.. table:: **Table 4** PluginTemplateSpec

   +-----------------------+-----------------------------------------------------------------------------------------------------------+---------------------------------+
   | Parameter             | Type                                                                                                      | Description                     |
   +=======================+===========================================================================================================+=================================+
   | type                  | String                                                                                                    | Plug-in template type. Options: |
   |                       |                                                                                                           |                                 |
   |                       |                                                                                                           | -  **npuDriver**: NPU driver    |
   |                       |                                                                                                           |                                 |
   |                       |                                                                                                           | -  **gpuDriver**: GPU driver    |
   |                       |                                                                                                           |                                 |
   |                       |                                                                                                           | -  **ccePlugin**: CCE plug-in   |
   |                       |                                                                                                           |                                 |
   |                       |                                                                                                           | -  **helm**: Helm template      |
   |                       |                                                                                                           |                                 |
   |                       |                                                                                                           | -  **icAgent**: ICAgent         |
   +-----------------------+-----------------------------------------------------------------------------------------------------------+---------------------------------+
   | description           | String                                                                                                    | Plug-in template description    |
   +-----------------------+-----------------------------------------------------------------------------------------------------------+---------------------------------+
   | versions              | Map<String,\ :ref:`PluginTemplateVersion <en-us_topic_0000002044058268__response_plugintemplateversion>`> | Plug-in template versions       |
   +-----------------------+-----------------------------------------------------------------------------------------------------------+---------------------------------+

.. _en-us_topic_0000002044058268__response_plugintemplateversion:

.. table:: **Table 5** PluginTemplateVersion

   ========= ====== ===================
   Parameter Type   Description
   ========= ====== ===================
   detail    String Version description
   ========= ====== ===================

**Status code: 404**

.. table:: **Table 6** Response body parameters

   +-----------------------+-----------------------+-----------------------+
   | Parameter             | Type                  | Description           |
   +=======================+=======================+=======================+
   | error_code            | String                | Error code            |
   |                       |                       |                       |
   |                       |                       | Minimum: **8**        |
   |                       |                       |                       |
   |                       |                       | Maximum: **36**       |
   +-----------------------+-----------------------+-----------------------+
   | error_msg             | String                | Error message         |
   |                       |                       |                       |
   |                       |                       | Minimum: **2**        |
   |                       |                       |                       |
   |                       |                       | Maximum: **512**      |
   +-----------------------+-----------------------+-----------------------+

Example Requests
----------------

None

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "apiVersion" : "v1",
     "kind" : "PluginTemplate",
     "metadata" : {
       "name" : "npu-driver"
     },
     "spec" : {
       "type" : "npuDriver",
       "description" : "npu driver"
     },
     "versions" : {
       "78-21.0.2" : {
         "detail" : "c78driver&firmware"
       },
       "77-21.0.cr1" : {
         "detail" : "c77driver&firmware"
       }
     }
   }

**Status code: 404**

Not found

.. code-block::

   {
     "error_code" : "ModelArts.50005101",
     "error_msg" : "Plugintemplate {name} not found."
   }

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
200         OK
404         Not found
=========== ===========

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
