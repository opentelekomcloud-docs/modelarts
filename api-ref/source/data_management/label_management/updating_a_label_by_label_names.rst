.. _UpdateLabel:

Updating a Label by Label Names
===============================

Function
--------

This API is used to update a label by label names.

URI
---

PUT /v2/{project_id}/datasets/{dataset_id}/data-annotations/labels/{label_name}

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

   +-----------------+-----------------+-----------------+-----------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                             |
   +=================+=================+=================+=========================================+
   | label_type      | No              | Integer         | Label type. The options are as follows: |
   |                 |                 |                 |                                         |
   |                 |                 |                 | -  **0**: image classification          |
   |                 |                 |                 |                                         |
   |                 |                 |                 | -  **1**: object detection              |
   |                 |                 |                 |                                         |
   |                 |                 |                 | -  **100**: text classification         |
   |                 |                 |                 |                                         |
   |                 |                 |                 | -  **101**: named entity recognition    |
   |                 |                 |                 |                                         |
   |                 |                 |                 | -  **102**: text triplet relationship   |
   |                 |                 |                 |                                         |
   |                 |                 |                 | -  **103**: text triplet entity         |
   |                 |                 |                 |                                         |
   |                 |                 |                 | -  **200**: speech classification       |
   |                 |                 |                 |                                         |
   |                 |                 |                 | -  **201**: speech content              |
   |                 |                 |                 |                                         |
   |                 |                 |                 | -  **202**: speech paragraph labeling   |
   |                 |                 |                 |                                         |
   |                 |                 |                 | -  **600**: video classification        |
   +-----------------+-----------------+-----------------+-----------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request body parameters

   +--------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                | Mandatory       | Type            | Description                                                                                                                                                                                                    |
   +==========================+=================+=================+================================================================================================================================================================================================================+
   | @modelarts:color         | No              | String          | Default attribute: Label color, which is a hexadecimal code of the color. By default, this parameter is left blank. Example: **#FFFFF0**.                                                                      |
   +--------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | @modelarts:default_shape | No              | String          | Default attribute: Default shape of an object detection label (dedicated attribute). By default, this parameter is left blank. The options are as follows:                                                     |
   |                          |                 |                 |                                                                                                                                                                                                                |
   |                          |                 |                 | -  **bndbox**: rectangle                                                                                                                                                                                       |
   |                          |                 |                 |                                                                                                                                                                                                                |
   |                          |                 |                 | -  **polygon**: polygon                                                                                                                                                                                        |
   |                          |                 |                 |                                                                                                                                                                                                                |
   |                          |                 |                 | -  **circle**: circle                                                                                                                                                                                          |
   |                          |                 |                 |                                                                                                                                                                                                                |
   |                          |                 |                 | -  **line**: straight line                                                                                                                                                                                     |
   |                          |                 |                 |                                                                                                                                                                                                                |
   |                          |                 |                 | -  **dashed**: dotted line                                                                                                                                                                                     |
   |                          |                 |                 |                                                                                                                                                                                                                |
   |                          |                 |                 | -  **point**: point                                                                                                                                                                                            |
   |                          |                 |                 |                                                                                                                                                                                                                |
   |                          |                 |                 | -  **polyline**: polyline                                                                                                                                                                                      |
   +--------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | @modelarts:from_type     | No              | String          | Default attribute: Type of the head entity in the triplet relationship label. This attribute must be specified when a relationship label is created. This parameter is used only for the text triplet dataset. |
   +--------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | @modelarts:rename_to     | No              | String          | Default attribute: The new name of the label.                                                                                                                                                                  |
   +--------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | @modelarts:shortcut      | No              | String          | Default attribute: Label shortcut key. By default, this parameter is left blank. For example: **D**.                                                                                                           |
   +--------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | @modelarts:to_type       | No              | String          | Default attribute: Type of the tail entity in the triplet relationship label. This attribute must be specified when a relationship label is created. This parameter is used only for the text triplet dataset. |
   +--------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 204**

.. table:: **Table 4** Response body parameters

   +-----------------------+-----------------------+------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                      |
   +=======================+=======================+==================================================================+
   | error_code            | String                | Error code.                                                      |
   +-----------------------+-----------------------+------------------------------------------------------------------+
   | error_msg             | String                | Error message.                                                   |
   +-----------------------+-----------------------+------------------------------------------------------------------+
   | success               | Boolean               | Whether the operation is successful. The options are as follows: |
   |                       |                       |                                                                  |
   |                       |                       | -  **true**: successful                                          |
   |                       |                       |                                                                  |
   |                       |                       | -  **false**: failed                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------+

Example Requests
----------------

Updating a Label by Label Names

.. code-block::

   {
     "@modelarts:color" : "#93c47d"
   }

Example Responses
-----------------

**Status code: 204**

No Content

.. code-block::

   { }

Status Codes
------------

=========== ============
Status Code Description
=========== ============
204         No Content
401         Unauthorized
403         Forbidden
404         Not Found
=========== ============

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
