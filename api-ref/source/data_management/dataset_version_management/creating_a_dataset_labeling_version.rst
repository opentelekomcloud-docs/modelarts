.. _CreateDatasetVersion:

Creating a Dataset Labeling Version
===================================

Function
--------

This API is used to create a dataset labeling version.

URI
---

POST /v2/{project_id}/datasets/{dataset_id}/versions

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                        |
   +============+===========+========+====================================================================================================================+
   | dataset_id | Yes       | String | Dataset ID.                                                                                                        |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <modelarts_03_0147>`. |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request body parameters

   +-----------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                   | Mandatory       | Type            | Description                                                                                                                                                       |
   +=============================+=================+=================+===================================================================================================================================================================+
   | clear_hard_property         | No              | Boolean         | Whether to clear hard example properties. The options are as follows:                                                                                             |
   |                             |                 |                 |                                                                                                                                                                   |
   |                             |                 |                 | -  **true**: Clear hard example properties. (Default value)                                                                                                       |
   |                             |                 |                 |                                                                                                                                                                   |
   |                             |                 |                 | -  **false**: Do not clear hard example properties.                                                                                                               |
   +-----------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description                 | No              | String          | Version description. The value is empty by default. The description contains 0 to 256 characters and does not support the following special characters: !<>=&"'   |
   +-----------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | export_images               | No              | Boolean         | Whether to export images to the version output directory during release. The options are as follows:                                                              |
   |                             |                 |                 |                                                                                                                                                                   |
   |                             |                 |                 | -  **true**: Export images to the version output directory.                                                                                                       |
   |                             |                 |                 |                                                                                                                                                                   |
   |                             |                 |                 | -  **false**: Do not export images to the version output directory. (Default value)                                                                               |
   +-----------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | remove_sample_usage         | No              | Boolean         | Whether to clear the existing usage information of a dataset during release. The options are as follows:                                                          |
   |                             |                 |                 |                                                                                                                                                                   |
   |                             |                 |                 | -  **true**: Clear the existing usage information of a dataset. (Default value)                                                                                   |
   |                             |                 |                 |                                                                                                                                                                   |
   |                             |                 |                 | -  **false**: Do not clear the existing usage information of a dataset.                                                                                           |
   +-----------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | train_evaluate_sample_ratio | No              | String          | Split training and verification ratio during version release. The default value is **1.00**, indicating that all labeled samples are split into the training set. |
   +-----------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version_format              | No              | String          | Format of a dataset version. The options are as follows:                                                                                                          |
   |                             |                 |                 |                                                                                                                                                                   |
   |                             |                 |                 | -  **Default**: default format                                                                                                                                    |
   |                             |                 |                 |                                                                                                                                                                   |
   |                             |                 |                 | -  **CarbonData**: CarbonData (supported only by table datasets)                                                                                                  |
   |                             |                 |                 |                                                                                                                                                                   |
   |                             |                 |                 | -  **CSV**: CSV                                                                                                                                                   |
   +-----------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version_name                | No              | String          | Version name. The value contains 1 to 32 characters. Only letters, digits, underscores (_), and hyphens (-) are allowed.                                          |
   +-----------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | with_column_header          | No              | Boolean         | Whether to write the column name in the first line of the CSV file during release. This field is valid for the table dataset. The options are as follows:         |
   |                             |                 |                 |                                                                                                                                                                   |
   |                             |                 |                 | -  **true**: Write the column name in the first line of the CSV file. (Default value)                                                                             |
   |                             |                 |                 |                                                                                                                                                                   |
   |                             |                 |                 | -  **false**: Do not write the column name in the first line of the CSV file.                                                                                     |
   +-----------------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 201**

.. table:: **Table 3** Response body parameters

   ========== ====== ===================
   Parameter  Type   Description
   ========== ====== ===================
   version_id String Dataset version ID.
   ========== ====== ===================

Example Requests
----------------

Creating a Dataset Labeling Version

.. code-block::

   {
     "version_name" : "V004",
     "version_format" : "Default",
     "description" : "",
     "clear_hard_property" : true
   }

Example Responses
-----------------

**Status code: 201**

Created

.. code-block::

   {
     "version_id" : "sntOdOuB0D9C6fC4TXs"
   }

Status Codes
------------

=========== ============
Status Code Description
=========== ============
201         Created
401         Unauthorized
403         Forbidden
404         Not Found
=========== ============

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
