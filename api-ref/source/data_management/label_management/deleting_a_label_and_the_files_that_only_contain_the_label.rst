.. _DeleteLabelAndSamples:

Deleting a Label and the Files that Only Contain the Label
==========================================================

Function
--------

This API is used to delete a label and the files that only contain this label.

URI
---

DELETE /v2/{project_id}/datasets/{dataset_id}/data-annotations/labels/{label_name}

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                        |
   +============+===========+========+====================================================================================================================+
   | dataset_id | Yes       | String | Dataset ID.                                                                                                        |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | label_name | Yes       | String | Label name.                                                                                                        |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <modelarts_03_0147>`. |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                            |
   +=================+=================+=================+========================================================================+
   | delete_source   | No              | Boolean         | Whether to delete the sample source files. The options are as follows: |
   |                 |                 |                 |                                                                        |
   |                 |                 |                 | -  **true**: Delete the sample source files.                           |
   |                 |                 |                 |                                                                        |
   |                 |                 |                 | -  **false**: Do not delete the sample source files. (Default value)   |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------+
   | label_type      | No              | Integer         | Label type. The options are as follows:                                |
   |                 |                 |                 |                                                                        |
   |                 |                 |                 | -  **0**: image classification                                         |
   |                 |                 |                 |                                                                        |
   |                 |                 |                 | -  **1**: object detection                                             |
   |                 |                 |                 |                                                                        |
   |                 |                 |                 | -  **100**: text classification                                        |
   |                 |                 |                 |                                                                        |
   |                 |                 |                 | -  **101**: named entity recognition                                   |
   |                 |                 |                 |                                                                        |
   |                 |                 |                 | -  **102**: text triplet relationship                                  |
   |                 |                 |                 |                                                                        |
   |                 |                 |                 | -  **103**: text triplet entity                                        |
   |                 |                 |                 |                                                                        |
   |                 |                 |                 | -  **200**: speech classification                                      |
   |                 |                 |                 |                                                                        |
   |                 |                 |                 | -  **201**: speech content                                             |
   |                 |                 |                 |                                                                        |
   |                 |                 |                 | -  **202**: speech paragraph labeling                                  |
   |                 |                 |                 |                                                                        |
   |                 |                 |                 | -  **600**: video classification                                       |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 204**

.. table:: **Table 3** Response body parameters

   +-----------------------+-----------------------+------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                            |
   +=======================+=======================+========================================================================+
   | error_code            | String                | Error code.                                                            |
   +-----------------------+-----------------------+------------------------------------------------------------------------+
   | error_msg             | String                | Error message.                                                         |
   +-----------------------+-----------------------+------------------------------------------------------------------------+
   | success               | Boolean               | Check whether the operation is successful. The options are as follows: |
   |                       |                       |                                                                        |
   |                       |                       | -  **true**: The operation is successful.                              |
   |                       |                       |                                                                        |
   |                       |                       | -  **false**: The operation is failed.                                 |
   +-----------------------+-----------------------+------------------------------------------------------------------------+

Example Requests
----------------

Deleting a Label and the Files that Only Contain the Label

.. code-block::

   DELETE https://{endpoint}/v2/{project_id}/datasets/WxCREuCkBSAlQr9xrde/data-annotations/labels/%E8%8D%89%E8%8E%93

Example Responses
-----------------

**Status code: 204**

No Content

.. code-block::

   {
     "success" : true
   }

Status Codes
------------

=========== ============
Status Code Description
=========== ============
204         No Content
401         Unauthorized
403         Forbidden
=========== ============

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
