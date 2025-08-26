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
   | metadata              | :ref:`PluginTemplateMetadata <en-us_topic_0000002340898514__response_plugintemplatemetadata>` object | Plug-in template metadata               |
   +-----------------------+------------------------------------------------------------------------------------------------------+-----------------------------------------+
   | spec                  | :ref:`PluginTemplateSpec <en-us_topic_0000002340898514__response_plugintemplatespec>` object         | Plug-in template specifications         |
   +-----------------------+------------------------------------------------------------------------------------------------------+-----------------------------------------+

.. _en-us_topic_0000002340898514__response_plugintemplatemetadata:

.. table:: **Table 3** PluginTemplateMetadata

   +-------------+--------------------+----------------------------------------------------------------+
   | Parameter   | Type               | Description                                                    |
   +=============+====================+================================================================+
   | name        | String             | Plug-in template name                                          |
   +-------------+--------------------+----------------------------------------------------------------+
   | annotations | Map<String,String> | Plug-in template annotations in the format of key-value pairs. |
   +-------------+--------------------+----------------------------------------------------------------+

.. _en-us_topic_0000002340898514__response_plugintemplatespec:

.. table:: **Table 4** PluginTemplateSpec

   +-----------------------+---------------------------------------------------------------------------------------------------------------+----------------------------------------------------+
   | Parameter             | Type                                                                                                          | Description                                        |
   +=======================+===============================================================================================================+====================================================+
   | type                  | String                                                                                                        | Plug-in template type. The options are as follows: |
   |                       |                                                                                                               |                                                    |
   |                       |                                                                                                               | -  **npu-river**: NPU driver                       |
   |                       |                                                                                                               |                                                    |
   |                       |                                                                                                               | -  **gpu-driver**: GPU driver                      |
   +-----------------------+---------------------------------------------------------------------------------------------------------------+----------------------------------------------------+
   | description           | String                                                                                                        | Plug-in template description                       |
   +-----------------------+---------------------------------------------------------------------------------------------------------------+----------------------------------------------------+
   | versions              | Map<String,\ :ref:`PluginTemplateVersionV2 <en-us_topic_0000002340898514__response_plugintemplateversionv2>`> | Plug-in template versions                          |
   +-----------------------+---------------------------------------------------------------------------------------------------------------+----------------------------------------------------+

.. _en-us_topic_0000002340898514__response_plugintemplateversionv2:

.. table:: **Table 5** PluginTemplateVersionV2

   ================= ====== ========================================
   Parameter         Type   Description
   ================= ====== ========================================
   version           String Version number of the plug-in template.
   creationTimestamp String Creation time.
   inputs            Object Plug-in installation parameters.
   translate         Object Translation information used by the GUI.
   description       String Version description.
   detail            String Version description.
   ================= ====== ========================================

**Status code: 404**

.. table:: **Table 6** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   error_code String Error code
   error_msg  String Error message
   ========== ====== =============

Example Requests
----------------

The following is an example of how to query plug-in template details.

.. code-block::

   https://{endpoint}/v1/{project_id}/plugintemplates/{plugintemplate_name}

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
