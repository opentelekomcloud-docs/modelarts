Obtaining Sample Search Condition
=================================

Function
--------

This API is used to obtain sample search condition.

URI
---

GET /v2/{project_id}/datasets/{dataset_id}/data-annotations/search-condition

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                                                |
   +============+===========+========+============================================================================================================================================================+
   | dataset_id | Yes       | String | Dataset ID.                                                                                                                                                |
   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see `Obtaining a Project ID <../../common_parameters/obtaining_a_project_id_and_name.html>`__. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**



.. _ListSearchresponseListSearchResp:

.. table:: **Table 2** Response body parameters

   +-----------+-------------------------------------------------------+----------------------------------------+
   | Parameter | Type                                                  | Description                            |
   +===========+=======================================================+========================================+
   | labelers  | Array of strings                                      | List of labeling team members.         |
   +-----------+-------------------------------------------------------+----------------------------------------+
   | labels    | Array of `Label <#listsearchresponselabel>`__ objects | Label list.                            |
   +-----------+-------------------------------------------------------+----------------------------------------+
   | metadata  | Map<String,Array<String>>                             | Attribute key-value pair of a dataset. |
   +-----------+-------------------------------------------------------+----------------------------------------+



.. _ListSearchresponseLabel:

.. table:: **Table 3** Label

   +-----------------------+-------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                    | Description                                                                                                                      |
   +=======================+=========================================================================+==================================================================================================================================+
   | attributes            | Array of `LabelAttribute <#listsearchresponselabelattribute>`__ objects | Multi-dimensional attribute of a label. For example, if the label is music, attributes such as style and artist may be included. |
   +-----------------------+-------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                                                                  | Label name.                                                                                                                      |
   +-----------------------+-------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | property              | `LabelProperty <#listsearchresponselabelproperty>`__ object             | Basic attribute key-value pair of a label, such as color and shortcut keys.                                                      |
   +-----------------------+-------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | type                  | Integer                                                                 | Label type. The options are as follows:                                                                                          |
   |                       |                                                                         |                                                                                                                                  |
   |                       |                                                                         | -  **0**: image classification                                                                                                   |
   |                       |                                                                         |                                                                                                                                  |
   |                       |                                                                         | -  **1**: object detection                                                                                                       |
   |                       |                                                                         |                                                                                                                                  |
   |                       |                                                                         | -  **100**: text classification                                                                                                  |
   |                       |                                                                         |                                                                                                                                  |
   |                       |                                                                         | -  **101**: named entity recognition                                                                                             |
   |                       |                                                                         |                                                                                                                                  |
   |                       |                                                                         | -  **102**: text triplet relationship                                                                                            |
   |                       |                                                                         |                                                                                                                                  |
   |                       |                                                                         | -  **103**: text triplet entity                                                                                                  |
   |                       |                                                                         |                                                                                                                                  |
   |                       |                                                                         | -  **200**: speech classification                                                                                                |
   |                       |                                                                         |                                                                                                                                  |
   |                       |                                                                         | -  **201**: speech content                                                                                                       |
   |                       |                                                                         |                                                                                                                                  |
   |                       |                                                                         | -  **202**: speech paragraph labeling                                                                                            |
   |                       |                                                                         |                                                                                                                                  |
   |                       |                                                                         | -  **600**: video classification                                                                                                 |
   +-----------------------+-------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------+



.. _ListSearchresponseLabelAttribute:

.. table:: **Table 4** LabelAttribute

   +-----------------------+-----------------------------------------------------------------------------------+---------------------------------------------------+
   | Parameter             | Type                                                                              | Description                                       |
   +=======================+===================================================================================+===================================================+
   | default_value         | String                                                                            | Default value of a label attribute.               |
   +-----------------------+-----------------------------------------------------------------------------------+---------------------------------------------------+
   | id                    | String                                                                            | Label attribute ID.                               |
   +-----------------------+-----------------------------------------------------------------------------------+---------------------------------------------------+
   | name                  | String                                                                            | Label attribute name.                             |
   +-----------------------+-----------------------------------------------------------------------------------+---------------------------------------------------+
   | type                  | String                                                                            | Label attribute type. The options are as follows: |
   |                       |                                                                                   |                                                   |
   |                       |                                                                                   | -  **text**: text                                 |
   |                       |                                                                                   |                                                   |
   |                       |                                                                                   | -  **select**: single-choice drop-down list       |
   +-----------------------+-----------------------------------------------------------------------------------+---------------------------------------------------+
   | values                | Array of `LabelAttributeValue <#listsearchresponselabelattributevalue>`__ objects | List of label attribute values.                   |
   +-----------------------+-----------------------------------------------------------------------------------+---------------------------------------------------+



.. _ListSearchresponseLabelAttributeValue:

.. table:: **Table 5** LabelAttributeValue

   ========= ====== =========================
   Parameter Type   Description
   ========= ====== =========================
   id        String Label attribute value ID.
   value     String Label attribute value.
   ========= ====== =========================



.. _ListSearchresponseLabelProperty:

.. table:: **Table 6** LabelProperty

   +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                | Type                  | Description                                                                                                                                                                                                    |
   +==========================+=======================+================================================================================================================================================================================================================+
   | @modelarts:color         | String                | Default attribute: Label color, which is a hexadecimal code of the color. By default, this parameter is left blank. Example: **#FFFFF0**.                                                                      |
   +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | @modelarts:default_shape | String                | Default attribute: Default shape of an object detection label (dedicated attribute). By default, this parameter is left blank. The options are as follows:                                                     |
   |                          |                       |                                                                                                                                                                                                                |
   |                          |                       | -  **bndbox**: rectangle                                                                                                                                                                                       |
   |                          |                       |                                                                                                                                                                                                                |
   |                          |                       | -  **polygon**: polygon                                                                                                                                                                                        |
   |                          |                       |                                                                                                                                                                                                                |
   |                          |                       | -  **circle**: circle                                                                                                                                                                                          |
   |                          |                       |                                                                                                                                                                                                                |
   |                          |                       | -  **line**: straight line                                                                                                                                                                                     |
   |                          |                       |                                                                                                                                                                                                                |
   |                          |                       | -  **dashed**: dotted line                                                                                                                                                                                     |
   |                          |                       |                                                                                                                                                                                                                |
   |                          |                       | -  **point**: point                                                                                                                                                                                            |
   |                          |                       |                                                                                                                                                                                                                |
   |                          |                       | -  **polyline**: polyline                                                                                                                                                                                      |
   +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | @modelarts:from_type     | String                | Default attribute: Type of the head entity in the triplet relationship label. This attribute must be specified when a relationship label is created. This parameter is used only for the text triplet dataset. |
   +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | @modelarts:rename_to     | String                | Default attribute: The new name of the label.                                                                                                                                                                  |
   +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | @modelarts:shortcut      | String                | Default attribute: Label shortcut key. By default, this parameter is left blank. For example: **D**.                                                                                                           |
   +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | @modelarts:to_type       | String                | Default attribute: Type of the tail entity in the triplet relationship label. This attribute must be specified when a relationship label is created. This parameter is used only for the text triplet dataset. |
   +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

Obtaining Sample Search Condition

.. code-block::

   GET https://{endpoint}/v2/{project_id}/datasets/{dataset_id}/data-annotations/search-condition

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "labels" : [ {
       "name" : "Cat",
       "type" : 0,
       "property" : {
         "@modelarts:color" : "#3399ff"
       }
     }, {
       "name" : "Dog",
       "type" : 0,
       "property" : {
         "@modelarts:color" : "#3399ff"
       }
     } ],
     "metadata" : { },
     "labelers" : [ "human/test_123/test_123", "human/xxx@xxx.com", "human/xxx@xxx.com" ]
   }

Status Codes
------------



.. _ListSearchstatuscode:

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

See `Error Codes <../../common_parameters/error_codes.html>`__.


