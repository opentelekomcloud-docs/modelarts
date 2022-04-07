.. _GetProcessorTaskItems:

Querying the Algorithm Type for Data Processing
===============================================

Function
--------

This API is used to query the algorithm type for data processing.

URI
---

GET /v2/{project_id}/processor-tasks/items

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                        |
   +============+===========+========+====================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <modelarts_03_0147>`. |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   +-----------+-----------------------------------------------------------------------------------------------+----------------------+
   | Parameter | Type                                                                                          | Description          |
   +===========+===============================================================================================+======================+
   | items     | Array of :ref:`ProcessorTaskItem <getprocessortaskitems__response_processortaskitem>` objects | Algorithm type list. |
   +-----------+-----------------------------------------------------------------------------------------------+----------------------+
   | total     | Integer                                                                                       | Total number.        |
   +-----------+-----------------------------------------------------------------------------------------------+----------------------+

.. _getprocessortaskitems__response_processortaskitem:

.. table:: **Table 3** ProcessorTaskItem

   =========== ====== ==================================
   Parameter   Type   Description
   =========== ====== ==================================
   label_en    String English name of an algorithm type.
   label_zh    String Chinese name of an algorithm type.
   template_id String Algorithm type ID.
   =========== ====== ==================================

Example Requests
----------------

Querying the List of the Algorithm Type for Data Processing

.. code-block::

   GET https://{endpoint}/v2/{project_id}/processor-tasks/items

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "total" : 4,
     "items" : [ {
       "template_id" : "sys_data_cleaning",
       "label_zh" : "label_zh to translate",
       "label_en" : "data cleaning"
     }, {
       "template_id" : "sys_data_validation",
       "label_zh" : "label_zh to translate",
       "label_en" : "data validation"
     }, {
       "template_id" : "sys_data_selection",
       "label_zh" : "label_zh to translate",
       "label_en" : "data selection"
     }, {
       "template_id" : "sys_data_augmentation",
       "label_zh" : "label_zh to translate",
       "label_en" : "data augmentation"
     } ]
   }

Status Codes
------------

=========== ============
Status Code Description
=========== ============
200         OK
401         Unauthorized
403         Forbidden
404         Not Found
=========== ============

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
