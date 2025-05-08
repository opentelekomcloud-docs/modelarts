:original_name: ShowAutoSearchYamlTemplatesInfo.html

.. _ShowAutoSearchYamlTemplatesInfo:

Obtaining Information About the YAML Template of an Auto Search Job
===================================================================

Function
--------

This API is used to obtain information about the YAML template of an auto search job.

URI
---

GET /v2/{project_id}/training-jobs/autosearch/yaml-templates

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

   +----------------+-------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------+
   | Parameter      | Type                                                                                                                    | Description                                   |
   +================+=========================================================================================================================+===============================================+
   | yaml_templates | Array of :ref:`YamlTemplate <en-us_topic_0000002233886834__en-us_topic_0000002091201373_response_yamltemplate>` objects | Directories and file names of all YAML files. |
   +----------------+-------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------+

.. _en-us_topic_0000002233886834__en-us_topic_0000002091201373_response_yamltemplate:

.. table:: **Table 3** YamlTemplate

   +-------------------+------------------+-----------------------------------------------------------+
   | Parameter         | Type             | Description                                               |
   +===================+==================+===========================================================+
   | algorithm_type_en | String           | AutoSearch algorithm type, which is described in English. |
   +-------------------+------------------+-----------------------------------------------------------+
   | algorithm_type_zh | String           | AutoSearch algorithm type                                 |
   +-------------------+------------------+-----------------------------------------------------------+
   | algorithm_names   | Array of strings | Names of all algorithms of this type.                     |
   +-------------------+------------------+-----------------------------------------------------------+

Example Requests
----------------

The following shows how to query information about the YAML configuration template of an auto search job.

.. code-block:: text

   GET https://endpoint/v2/{project_id}/training-jobs/autosearch/yaml-templates

Example Responses
-----------------

**Status code: 200**

ok

.. code-block::

   {
     "yaml_templates" : [ {
       "algorithm_type_en" : "hpo",
       "algorithm_type_zh" : "algorithm_type_zh to translate",
       "algorithm_names" : [ "Anneal", "Bayes", "DragonFly", "FixNorm", "GridSearch", "TPE" ]
     }, {
       "algorithm_type_en" : "nas",
       "algorithm_type_zh" : "algorithm_type_zh to translate",
       "algorithm_names" : [ "AutoBSS", "AutoEvo", "AutoTopo", "MBNAS" ]
     }, {
       "algorithm_type_en" : "augment",
       "algorithm_type_zh" : "algorithm_type_zh to translate",
       "algorithm_names" : [ "AdvAutoAugment", "AutoAugment" ]
     }, {
       "algorithm_type_en" : "compression",
       "algorithm_type_zh" : "algorithm_type_zh to translate",
       "algorithm_names" : [ "AutoCompress" ]
     } ]
   }

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
200         ok
=========== ===========

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
