:original_name: DeleteModel.html

.. _DeleteModel:

Deleting an AI application
==========================

Function
--------

This interface is used to delete an AI application based on the AI application ID. When cascade is set to true, the AI application specified by the AI application ID and other AI applications with the same name but different versions as the specified AI application are deleted. By default, only the AI application corresponding to the current AI application ID is deleted.

URI
---

DELETE /v1/{project_id}/models/{model_id}

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                              |
   +============+===========+========+==========================================================================================+
   | model_id   | Yes       | String | ID of the AI application to be deleted.                                                  |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------+-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                                                                                                                                                                                                                                                                                                                                                                                        |
   +===========+===========+=========+====================================================================================================================================================================================================================================================================================================================================================================================================================+
   | cascade   | No        | Boolean | Indicates whether to perform cascading deletion. The default value is false, indicating that only the model with the specified model ID is deleted. If this parameter is set to true, the model specified by the model ID is deleted, and all models with the same name but different versions as the specified model are deleted. A maximum of 20 models can be deleted at a time. Excess models are not deleted. |
   +-----------+-----------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                           |
   +==============+===========+========+=======================================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. It can be obtained by calling the IAM API that is used to obtain a user token. The value of **X-Subject-Token** in the response header is the user token. |
   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +---------------------+------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------+
   | Parameter           | Type                                                                                                                         | Description                                                         |
   +=====================+==============================================================================================================================+=====================================================================+
   | delete_success_list | Array of strings                                                                                                             | ID list of models successfully deleted                              |
   +---------------------+------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------+
   | delete_failed_list  | Array of :ref:`DeleteModelResponseFailedList <en-us_topic_0000002042965000__response_deletemodelresponsefailedlist>` objects | ID of the model that fails to be deleted and the failure cause list |
   +---------------------+------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------+

.. _en-us_topic_0000002042965000__response_deletemodelresponsefailedlist:

.. table:: **Table 5** DeleteModelResponseFailedList

   ========== ====== ===========================================
   Parameter  Type   Description
   ========== ====== ===========================================
   error_msg  String Error message of the model deletion failure
   error_code String Error code of the model deletion failure
   model_id   String ID of a model that fails to be deleted
   ========== ====== ===========================================

Example Requests
----------------

.. code-block:: text

   DELETE https://{endpoint}/v1/{project_id}/models/{model_id}

Example Responses
-----------------

**Status code: 200**

Message indicating a successful deletion or a deletion failure

.. code-block::

   {
     "delete_success_list" : [ "10eb0091-887f-4839-9929-cbc884f1e20e" ],
     "delete_failed_list" : [ {
       "error_msg" : "Failed to delete model because the model (759645d9-3672-4db1-bb6d-49ed58b84e10) has been used to deploy a service.",
       "error_code" : "ModelArts.3009",
       "model_id" : "e527d311-a947-46da-a6e0-66c49945dfaa"
     } ]
   }

Status Codes
------------

+-------------+----------------------------------------------------------------+
| Status Code | Description                                                    |
+=============+================================================================+
| 200         | Message indicating a successful deletion or a deletion failure |
+-------------+----------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
