:original_name: DeleteSamples.html

.. _DeleteSamples:

Deleting Samples in Batches
===========================

Function
--------

This API is used to delete samples in batches.

Debugging
---------

You can debug this API through automatic authentication in or use the SDK sample code generated by API Explorer.

URI
---

POST /v2/{project_id}/datasets/{dataset_id}/data-annotations/samples/delete

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                               |
   +============+===========+========+===========================================================================================================================+
   | dataset_id | Yes       | String | Dataset ID.                                                                                                               |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+
   | project_id | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request body parameters

   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                                                                                              |
   +=================+=================+==================+==========================================================================================================================================================================================================================+
   | delete_source   | No              | Boolean          | Whether to delete the source file. This field is valid for non-text datasets. (A text dataset is the entire text file. Therefore, deleting a piece of data from the text file does not affect the source text.) Options: |
   |                 |                 |                  |                                                                                                                                                                                                                          |
   |                 |                 |                  | -  **false**: Do not delete the source file. (Default value)                                                                                                                                                             |
   |                 |                 |                  |                                                                                                                                                                                                                          |
   |                 |                 |                  | -  **true**: Delete the source file. (Note: This operation may affect the dataset versions or other datasets that have used these files. As a result, the page display, training, or inference is abnormal.)             |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | samples         | No              | Array of strings | Sample ID list.                                                                                                                                                                                                          |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------------------+----------------------------------------------------------------------------------------------+-----------------------------------------------------+
   | Parameter             | Type                                                                                         | Description                                         |
   +=======================+==============================================================================================+=====================================================+
   | error_code            | String                                                                                       | Error code.                                         |
   +-----------------------+----------------------------------------------------------------------------------------------+-----------------------------------------------------+
   | error_msg             | String                                                                                       | Error message.                                      |
   +-----------------------+----------------------------------------------------------------------------------------------+-----------------------------------------------------+
   | results               | Array of :ref:`BatchResponse <en-us_topic_0000001909907504__response_batchresponse>` objects | Response list for deleting a sample in batches.     |
   +-----------------------+----------------------------------------------------------------------------------------------+-----------------------------------------------------+
   | success               | Boolean                                                                                      | Check whether the operation is successful. Options: |
   |                       |                                                                                              |                                                     |
   |                       |                                                                                              | -  **true**: The operation is successful.           |
   |                       |                                                                                              |                                                     |
   |                       |                                                                                              | -  **false**: The operation is failed.              |
   +-----------------------+----------------------------------------------------------------------------------------------+-----------------------------------------------------+

.. _en-us_topic_0000001909907504__response_batchresponse:

.. table:: **Table 4** BatchResponse

   +-----------------------+-----------------------+-----------------------------------------------------+
   | Parameter             | Type                  | Description                                         |
   +=======================+=======================+=====================================================+
   | error_code            | String                | Error code.                                         |
   +-----------------------+-----------------------+-----------------------------------------------------+
   | error_msg             | String                | Error message.                                      |
   +-----------------------+-----------------------+-----------------------------------------------------+
   | success               | Boolean               | Check whether the operation is successful. Options: |
   |                       |                       |                                                     |
   |                       |                       | -  **true**: The operation is successful.           |
   |                       |                       |                                                     |
   |                       |                       | -  **false**: The operation is failed.              |
   +-----------------------+-----------------------+-----------------------------------------------------+

Example Requests
----------------

Deleting Samples in Batches

.. code-block::

   {
     "samples" : [ "9cb9bc9b34bf53b6ec9a84998b1711bf", "9ea63ef78d8c9037c9bcb12b477821bf" ]
   }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "success" : true
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
