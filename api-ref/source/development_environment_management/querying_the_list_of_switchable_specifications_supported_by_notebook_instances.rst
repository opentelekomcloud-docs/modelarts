:original_name: ShowSwitchableFlavors.html

.. _ShowSwitchableFlavors:

Querying the List of Switchable Specifications Supported by Notebook Instances
==============================================================================

Function
--------

This API is used to query the list of flavors that can be switched during notebook instance creation.

Constraints
-----------

None

URI
---

GET /v1/{project_id}/notebooks/{id}/flavors

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                             |
   +============+===========+========+=========================================================================================================+
   | id         | Yes       | String | Notebook instance ID, which can be obtained by calling the API for querying the notebook instance list. |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`.                |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------+-----------+---------+-------------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                           |
   +===========+===========+=========+=======================================================+
   | limit     | No        | Integer | Number of records on each page. (No limit by default) |
   +-----------+-----------+---------+-------------------------------------------------------+
   | offset    | No        | Integer | Start offset of the records on each page              |
   +-----------+-----------+---------+-------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------+-----------------------------------------------------------------------------------------------------------------------------+----------------------------------------------+
   | Parameter | Type                                                                                                                        | Description                                  |
   +===========+=============================================================================================================================+==============================================+
   | current   | Integer                                                                                                                     | Current page                                 |
   +-----------+-----------------------------------------------------------------------------------------------------------------------------+----------------------------------------------+
   | data      | Array of :ref:`NotebookFlavor <en-us_topic_0000002374896589__en-us_topic_0000002055322410_response_notebookflavor>` objects | Pagination data                              |
   +-----------+-----------------------------------------------------------------------------------------------------------------------------+----------------------------------------------+
   | flavors   | Array of :ref:`NotebookFlavor <en-us_topic_0000002374896589__en-us_topic_0000002055322410_response_notebookflavor>` objects | List of specifications that can be switched. |
   +-----------+-----------------------------------------------------------------------------------------------------------------------------+----------------------------------------------+
   | pages     | Integer                                                                                                                     | Total number of pages                        |
   +-----------+-----------------------------------------------------------------------------------------------------------------------------+----------------------------------------------+
   | size      | Integer                                                                                                                     | Number of records on each page               |
   +-----------+-----------------------------------------------------------------------------------------------------------------------------+----------------------------------------------+
   | total     | Long                                                                                                                        | Total number of records                      |
   +-----------+-----------------------------------------------------------------------------------------------------------------------------+----------------------------------------------+

.. _en-us_topic_0000002374896589__en-us_topic_0000002055322410_response_notebookflavor:

.. table:: **Table 4** NotebookFlavor

   +-----------------------+-------------------------------------------------------------------------------------------------------------+-------------------------------------------------+
   | Parameter             | Type                                                                                                        | Description                                     |
   +=======================+=============================================================================================================+=================================================+
   | arch                  | String                                                                                                      | Architecture type.                              |
   |                       |                                                                                                             |                                                 |
   |                       |                                                                                                             | -  **X86_64**                                   |
   |                       |                                                                                                             |                                                 |
   |                       |                                                                                                             | -  **AARCH64**                                  |
   +-----------------------+-------------------------------------------------------------------------------------------------------------+-------------------------------------------------+
   | billing               | :ref:`BillingInfo <en-us_topic_0000002374896589__en-us_topic_0000002055322410_response_billinginfo>` object | CDR information                                 |
   +-----------------------+-------------------------------------------------------------------------------------------------------------+-------------------------------------------------+
   | category              | String                                                                                                      | Processor type. Options:                        |
   |                       |                                                                                                             |                                                 |
   |                       |                                                                                                             | -  **CPU**                                      |
   |                       |                                                                                                             |                                                 |
   |                       |                                                                                                             | -  **GPU**                                      |
   +-----------------------+-------------------------------------------------------------------------------------------------------------+-------------------------------------------------+
   | description           | String                                                                                                      | Specification description                       |
   +-----------------------+-------------------------------------------------------------------------------------------------------------+-------------------------------------------------+
   | feature               | String                                                                                                      | Specification type. The options are as follows: |
   |                       |                                                                                                             |                                                 |
   |                       |                                                                                                             | -  DEFAULT: CodeLab specification.              |
   |                       |                                                                                                             |                                                 |
   |                       |                                                                                                             | -  NOTEBOOK: Notebook specifications.           |
   +-----------------------+-------------------------------------------------------------------------------------------------------------+-------------------------------------------------+
   | free                  | Boolean                                                                                                     | Specifies whether the flavor is free of charge. |
   +-----------------------+-------------------------------------------------------------------------------------------------------------+-------------------------------------------------+
   | gpu                   | :ref:`GPUInfo <en-us_topic_0000002374896589__en-us_topic_0000002055322410_response_gpuinfo>` object         | GPU information                                 |
   +-----------------------+-------------------------------------------------------------------------------------------------------------+-------------------------------------------------+
   | id                    | String                                                                                                      | Flavor ID                                       |
   +-----------------------+-------------------------------------------------------------------------------------------------------------+-------------------------------------------------+
   | memory                | Long                                                                                                        | Memory size                                     |
   +-----------------------+-------------------------------------------------------------------------------------------------------------+-------------------------------------------------+
   | name                  | String                                                                                                      | Flavor name                                     |
   +-----------------------+-------------------------------------------------------------------------------------------------------------+-------------------------------------------------+
   | sold_out              | Boolean                                                                                                     | Whether resources are sufficient.               |
   |                       |                                                                                                             |                                                 |
   |                       |                                                                                                             | -  **true**: Resources are insufficient.        |
   |                       |                                                                                                             |                                                 |
   |                       |                                                                                                             | -  **false**: Resources are sufficient.         |
   +-----------------------+-------------------------------------------------------------------------------------------------------------+-------------------------------------------------+
   | storages              | Array of strings                                                                                            | Storage type. Options:                          |
   |                       |                                                                                                             |                                                 |
   |                       |                                                                                                             | -  **EFS**                                      |
   |                       |                                                                                                             |                                                 |
   |                       |                                                                                                             | -  **EVS**                                      |
   +-----------------------+-------------------------------------------------------------------------------------------------------------+-------------------------------------------------+
   | vcpus                 | Integer                                                                                                     | Number of vCPUs                                 |
   +-----------------------+-------------------------------------------------------------------------------------------------------------+-------------------------------------------------+

.. _en-us_topic_0000002374896589__en-us_topic_0000002055322410_response_billinginfo:

.. table:: **Table 5** BillingInfo

   ========= ======= =============
   Parameter Type    Description
   ========= ======= =============
   code      String  Billing code.
   unit_num  Integer Billing unit.
   ========= ======= =============

.. _en-us_topic_0000002374896589__en-us_topic_0000002055322410_response_gpuinfo:

.. table:: **Table 6** GPUInfo

   ========== ======= ===============
   Parameter  Type    Description
   ========== ======= ===============
   gpu        Integer Number of GPUs.
   gpu_memory String  GPU memory.
   type       String  GPU type.
   ========== ======= ===============

Example Requests
----------------

.. code-block:: text

   GET https://{endpoint}/v1/{project_id}/notebooks/{id}/flavors

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "current" : 1,
     "data" : [ {
       "arch" : "aarch64",
       "billing" : {
         "code" : "modelarts.kat1.xlarge",
         "unit_num" : 2
       },
       "category" : "CPU",
       "description" : "The specification is suitable for deep learning code running and debugging",
       "feature" : "NOTEBOOK",
       "free" : false,
       "id" : "modelarts.bm.snt9.xlarge.2",
       "memory" : 201326592,
       "name" : "CPU: 48vCPUs 192GB",
       "sold_out" : false,
       "storages" : [ "EFS" ],
       "vcpus" : 48
     }, {
       "arch" : "aarch64",
       "billing" : {
         "code" : "modelarts.kat1.8xlarge",
         "unit_num" : 1
       },
       "category" : "CPU",
       "description" : "The specification is suitable for deep learning code running and debugging",
       "feature" : "NOTEBOOK",
       "free" : false,
       "id" : "modelarts.bm.snt9.xlarge.8",
       "memory" : 805306368,
       "name" : "CPU: 192vCPUs 768GB",
       "sold_out" : false,
       "storages" : [ "EFS" ],
       "vcpus" : 192
     } ],
     "flavors" : [ {
       "arch" : "aarch64",
       "billing" : {
         "code" : "modelarts.kat1.xlarge",
         "unit_num" : 2
       },
       "category" : "CPU",
       "description" : "The specification is suitable for deep learning code running and debugging",
       "feature" : "NOTEBOOK",
       "free" : false,
       "id" : "modelarts.bm.snt9.xlarge.2",
       "memory" : 201326592,
       "name" : "CPU: 48vCPUs 192GB",
       "sold_out" : false,
       "storages" : [ "EFS" ],
       "vcpus" : 48
     }, {
       "arch" : "aarch64",
       "billing" : {
         "code" : "modelarts.kat1.8xlarge",
         "unit_num" : 1
       },
       "category" : "CPU",
       "description" : "The specification is suitable for deep learning code running and debugging",
       "feature" : "NOTEBOOK",
       "free" : false,
       "id" : "modelarts.bm.snt9.xlarge.8",
       "memory" : 805306368,
       "name" : "CPU: 192vCPUs 768GB",
       "sold_out" : false,
       "storages" : [ "EFS" ],
       "vcpus" : 192
     } ],
     "pages" : 1,
     "size" : 2,
     "total" : 2
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
