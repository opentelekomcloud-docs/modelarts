.. _modelarts_03_0079:

Deleting a Model
================

Function
--------

This API is used to delete a model based on the model ID. When **cascade** is set to **true**, the model specified by the model ID and models of different versions with the same name as the specified model are deleted. By default, only the model with the specified model ID is deleted.

URI
---

DELETE /v1/{project_id}/models/{model_id}

:ref:`Table 1 <modelarts_03_0079__en-us_topic_0130168819_table16518993181628>` describes the required parameters.

.. _modelarts_03_0079__en-us_topic_0130168819_table16518993181628:

.. table:: **Table 1** Parameter description

   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                 |
   +============+===========+========+=============================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | model_id   | Yes       | String | ID of the model to be deleted                                                                                               |
   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Parameter description

   +-----------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                                                                                                                                                                                                                                                                                                                    |
   +===========+===========+=========+================================================================================================================================================================================================================================================================================================================================================+
   | cascade   | No        | Boolean | The default value is **false**, indicating that only the model with the specified model ID is deleted. The value **true** indicates that not only the model with the specified model ID but also all models with the same name but different versions as the specified model will be deleted. A maximum of 20 models can be deleted at a time. |
   +-----------+-----------+---------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Body
------------

None

Response Body
-------------

:ref:`Table 3 <modelarts_03_0079__en-us_topic_0130168819_table1954662185412>` describes the response parameters.

.. _modelarts_03_0079__en-us_topic_0130168819_table1954662185412:

.. table:: **Table 3** Parameter description

   +---------------------+---------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter           | Type                            | Description                                                                                                                             |
   +=====================+=================================+=========================================================================================================================================+
   | delete_success_list | String array                    | ID list of models successfully deleted                                                                                                  |
   +---------------------+---------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | delete_failed_list  | **DeleteModelFailResult** array | List of models that fail to be deleted. For details, see :ref:`Table 4 <modelarts_03_0079__en-us_topic_0130168819_table1198992710540>`. |
   +---------------------+---------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+

.. _modelarts_03_0079__en-us_topic_0130168819_table1198992710540:

.. table:: **Table 4** **DeleteModelFailResult** parameters

   ============= ====== ======================================
   Parameter     Type   Description
   ============= ====== ======================================
   model_id      String ID of a model that fails to be deleted
   error_code    String Error code of the deletion failure
   error_message String Error message of the deletion failure
   ============= ====== ======================================

Samples
-------

The following shows how to delete the model whose ID is **023e90be-7e2a-4169-bab4-1bc34ff0ca45** and all models of the same name but different versions.

-  Sample request

   .. code-block::

      DELETE    https://endpoint/v1/{project_id}/models/023e90be-7e2a-4169-bab4-1bc34ff0ca45?cascade=true

-  Sample response

   .. code-block::

      {
      "delete_success_list": ["fc9e88a1-0005-40b3-867e-7aee61449aeb", "f3f3ba0e-f073-454e-9e3f-14b7d786f45e"],
      "delete_failed_list": [
      {
      "model_id": "759645d9-3672-4db1-bb6d-49ed58b84e10",
      "error_code": "ModelArts.3009",
      "error_message": "Failed to delete model, model (759645d9-3672-4db1-bb6d-49ed58b84e10) already deploy service."
      }]
      }

Status Code
-----------

For details about the status code, see :ref:`Table 1 <modelarts_03_0094__en-us_topic_0132773864_table1450010510213>`.
