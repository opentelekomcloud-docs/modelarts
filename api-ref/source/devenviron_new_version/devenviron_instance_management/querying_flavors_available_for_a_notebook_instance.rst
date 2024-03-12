:original_name: ShowSwitchableFlavors.html

.. _ShowSwitchableFlavors:

Querying Flavors Available for a Notebook Instance
==================================================

Function
--------

This API is used to query the flavors available for a notebook instance.

Constraints
-----------

None

URI
---

GET /v1/{project_id}/notebooks/{id}/flavors

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+---------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                     |
   +============+===========+========+=================================================================================+
   | id         | Yes       | String | Notebook instance ID.                                                           |
   +------------+-----------+--------+---------------------------------------------------------------------------------+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID <modelarts_03_0147>`. |
   +------------+-----------+--------+---------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   +-----------+-----------------------------------------------------------------------------------------+-------------+
   | Parameter | Type                                                                                    | Description |
   +===========+=========================================================================================+=============+
   | flavors   | Array of :ref:`NotebookFlavor <showswitchableflavors__response_notebookflavor>` objects | Flavor list |
   +-----------+-----------------------------------------------------------------------------------------+-------------+

.. _showswitchableflavors__response_notebookflavor:

.. table:: **Table 3** NotebookFlavor

   +-----------------------+-------------------------------------------------------------------------+---------------------------------------------------------------------------+
   | Parameter             | Type                                                                    | Description                                                               |
   +=======================+=========================================================================+===========================================================================+
   | arch                  | String                                                                  | Architecture type. Options: - **X86_64** - **AARCH64**                    |
   +-----------------------+-------------------------------------------------------------------------+---------------------------------------------------------------------------+
   | ascend                | :ref:`AscendInfo <showswitchableflavors__response_ascendinfo>` object   | NPU information                                                           |
   +-----------------------+-------------------------------------------------------------------------+---------------------------------------------------------------------------+
   | billing               | :ref:`BillingInfo <showswitchableflavors__response_billinginfo>` object | Billing information                                                       |
   +-----------------------+-------------------------------------------------------------------------+---------------------------------------------------------------------------+
   | category              | String                                                                  | Processor type. Options: - **CPU** - **GPU** - **ASCEND**                 |
   +-----------------------+-------------------------------------------------------------------------+---------------------------------------------------------------------------+
   | description           | String                                                                  | Instance flavor description                                               |
   +-----------------------+-------------------------------------------------------------------------+---------------------------------------------------------------------------+
   | feature               | String                                                                  | Flavor category. Options: - **DEFAULT**: CodeLab - **NOTEBOOK**: Notebook |
   +-----------------------+-------------------------------------------------------------------------+---------------------------------------------------------------------------+
   | free                  | Boolean                                                                 | Free flavor or not                                                        |
   +-----------------------+-------------------------------------------------------------------------+---------------------------------------------------------------------------+
   | gpu                   | :ref:`GPUInfo <showswitchableflavors__response_gpuinfo>` object         | GPU information                                                           |
   +-----------------------+-------------------------------------------------------------------------+---------------------------------------------------------------------------+
   | id                    | String                                                                  | Flavor ID                                                                 |
   +-----------------------+-------------------------------------------------------------------------+---------------------------------------------------------------------------+
   | memory                | Long                                                                    | Memory size                                                               |
   +-----------------------+-------------------------------------------------------------------------+---------------------------------------------------------------------------+
   | name                  | String                                                                  | Flavor name                                                               |
   +-----------------------+-------------------------------------------------------------------------+---------------------------------------------------------------------------+
   | sold_out              | Boolean                                                                 | Whether the resources are sufficient. Options:                            |
   |                       |                                                                         |                                                                           |
   |                       |                                                                         | -  **true** indicates that the resources are insufficient.                |
   |                       |                                                                         | -  **false** indicates that the resources are sufficient.                 |
   +-----------------------+-------------------------------------------------------------------------+---------------------------------------------------------------------------+
   | storages              | Array of strings                                                        | Storage type supported by the flavor. Options:                            |
   |                       |                                                                         |                                                                           |
   |                       |                                                                         | -  **EVS**                                                                |
   |                       |                                                                         | -  **EFS**                                                                |
   +-----------------------+-------------------------------------------------------------------------+---------------------------------------------------------------------------+
   | vcpus                 | Integer                                                                 | Number of vCPUs                                                           |
   +-----------------------+-------------------------------------------------------------------------+---------------------------------------------------------------------------+

.. _showswitchableflavors__response_ascendinfo:

.. table:: **Table 4** AscendInfo

   ========== ======= ==============
   Parameter  Type    Description
   ========== ======= ==============
   npu        Integer Number of NPUs
   npu_memory String  NPU memory
   type       String  NPU type
   ========== ======= ==============

.. _showswitchableflavors__response_billinginfo:

.. table:: **Table 5** BillingInfo

   ========= ======= ============
   Parameter Type    Description
   ========= ======= ============
   code      String  Billing code
   unit_num  Integer Billing unit
   ========= ======= ============

.. _showswitchableflavors__response_gpuinfo:

.. table:: **Table 6** GPUInfo

   ========== ======= ==============
   Parameter  Type    Description
   ========== ======= ==============
   gpu        Integer Number of GPUs
   gpu_memory String  GPU memory
   type       String  GPU type
   ========== ======= ==============

Example Requests
----------------

None

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "flavors" : [ {
       "arch" : "X86_64",
       "feature" : "NOTEBOOK",
       "free" : false,
       "storages" : [ "EFS" ],
       "id" : "modelarts.vm.cpu.8u",
       "category" : "CPU",
       "vcpus" : 1,
       "memory" : 1048576,
       "name" : "CPU: 8vCPUs 32GB",
       "description" : "General computing-plus Intel CPU specifications, ideal for compute-intensive applications.",
       "billing" : {
         "code" : "modelarts.vm.cpu.2u",
         "unitNum" : 4
       },
       "sold_out" : false
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
