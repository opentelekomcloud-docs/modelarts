:original_name: ShowTrainingJobFlavors.html

.. _ShowTrainingJobFlavors:

Obtaining the General Specifications Supported by a Training Job
================================================================

Function
--------

This API is used to obtain the public flavors supported by a training job.

URI
---

GET /v2/{project_id}/training-job-flavors

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                              |
   +============+===========+========+==========================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                 |
   +=================+=================+=================+=============================================================================================================================+
   | flavor_type     | No              | String          | This API is used to obtain training job flavors. If this parameter is not specified, all flavors will be obtained. Options: |
   |                 |                 |                 |                                                                                                                             |
   |                 |                 |                 | -  **CPU**                                                                                                                  |
   |                 |                 |                 |                                                                                                                             |
   |                 |                 |                 | -  **GPU**                                                                                                                  |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-------------+------------------------------------------------------------------------------------------------+-----------------------------------------------------+
   | Parameter   | Type                                                                                           | Description                                         |
   +=============+================================================================================================+=====================================================+
   | total_count | Integer                                                                                        | Total number of resource flavors of a training job. |
   +-------------+------------------------------------------------------------------------------------------------+-----------------------------------------------------+
   | flavors     | Array of :ref:`FlavorResponse <en-us_topic_0000002079045733__response_flavorresponse>` objects | List of resource flavors of a training job.         |
   +-------------+------------------------------------------------------------------------------------------------+-----------------------------------------------------+

.. _en-us_topic_0000002079045733__response_flavorresponse:

.. table:: **Table 4** FlavorResponse

   +-----------------------+--------------------------------------------------------------------------------+-----------------------------------------------+
   | Parameter             | Type                                                                           | Description                                   |
   +=======================+================================================================================+===============================================+
   | flavor_id             | String                                                                         | ID of the resource flavor.                    |
   +-----------------------+--------------------------------------------------------------------------------+-----------------------------------------------+
   | flavor_name           | String                                                                         | Name of the resource flavor.                  |
   +-----------------------+--------------------------------------------------------------------------------+-----------------------------------------------+
   | max_num               | Integer                                                                        | Maximum number of nodes in a resource flavor. |
   +-----------------------+--------------------------------------------------------------------------------+-----------------------------------------------+
   | flavor_type           | String                                                                         | Resource flavor type. Options:                |
   |                       |                                                                                |                                               |
   |                       |                                                                                | -  **CPU**                                    |
   |                       |                                                                                |                                               |
   |                       |                                                                                | -  **GPU**                                    |
   +-----------------------+--------------------------------------------------------------------------------+-----------------------------------------------+
   | billing               | :ref:`billing <en-us_topic_0000002079045733__response_billing>` object         | Billing information of a resource flavor.     |
   +-----------------------+--------------------------------------------------------------------------------+-----------------------------------------------+
   | flavor_info           | :ref:`flavor_info <en-us_topic_0000002079045733__response_flavor_info>` object | Resource flavor details.                      |
   +-----------------------+--------------------------------------------------------------------------------+-----------------------------------------------+
   | attributes            | Map<String,String>                                                             | Other specification attributes.               |
   +-----------------------+--------------------------------------------------------------------------------+-----------------------------------------------+

.. _en-us_topic_0000002079045733__response_billing:

.. table:: **Table 5** billing

   ========= ======= ========================
   Parameter Type    Description
   ========= ======= ========================
   code      String  Billing code.
   unit_num  Integer Number of billing units.
   ========= ======= ========================

.. _en-us_topic_0000002079045733__response_flavor_info:

.. table:: **Table 6** flavor_info

   +-----------+----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type                                                                 | Description                                                                                                         |
   +===========+======================================================================+=====================================================================================================================+
   | max_num   | Integer                                                              | Maximum number of nodes that can be selected. The value **1** indicates that the distributed mode is not supported. |
   +-----------+----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | cpu       | :ref:`cpu <en-us_topic_0000002079045733__response_cpu>` object       | CPU specifications.                                                                                                 |
   +-----------+----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | gpu       | :ref:`gpu <en-us_topic_0000002079045733__response_gpu>` object       | GPU specifications.                                                                                                 |
   +-----------+----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | npu       | :ref:`npu <en-us_topic_0000002079045733__response_npu>` object       | Ascend specifications                                                                                               |
   +-----------+----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | memory    | :ref:`memory <en-us_topic_0000002079045733__response_memory>` object | Memory information.                                                                                                 |
   +-----------+----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | disk      | :ref:`disk <en-us_topic_0000002079045733__response_disk>` object     | Disk information.                                                                                                   |
   +-----------+----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002079045733__response_cpu:

.. table:: **Table 7** cpu

   ========= ======= =================
   Parameter Type    Description
   ========= ======= =================
   arch      String  CPU architecture.
   core_num  Integer Number of cores.
   ========= ======= =================

.. _en-us_topic_0000002079045733__response_gpu:

.. table:: **Table 8** gpu

   ============ ======= ===============
   Parameter    Type    Description
   ============ ======= ===============
   unit_num     Integer Number of GPUs.
   product_name String  Product name.
   memory       String  Memory.
   ============ ======= ===============

.. _en-us_topic_0000002079045733__response_npu:

.. table:: **Table 9** npu

   ============ ====== ===============
   Parameter    Type   Description
   ============ ====== ===============
   unit_num     String Number of NPUs.
   product_name String Product name.
   memory       String Memory.
   ============ ====== ===============

.. _en-us_topic_0000002079045733__response_memory:

.. table:: **Table 10** memory

   ========= ======= ============
   Parameter Type    Description
   ========= ======= ============
   size      Integer Memory size.
   unit      String  Memory size
   ========= ======= ============

.. _en-us_topic_0000002079045733__response_disk:

.. table:: **Table 11** disk

   ========= ======= ======================
   Parameter Type    Description
   ========= ======= ======================
   size      Integer Disk size.
   unit      String  Unit of the disk size.
   ========= ======= ======================

Example Requests
----------------

The following shows how to query the public CPU resource flavors of training jobs.

.. code-block:: text

   GET https://endpoint/v2/{project_id}/training-job-flavors?flavor_type=CPU

Example Responses
-----------------

**Status code: 200**

ok

.. code-block::

   {
     "total_count" : 2,
     "flavors" : [ {
       "flavor_id" : "modelarts.vm.cpu.2u",
       "flavor_name" : "Computing CPU(2U) instance",
       "flavor_type" : "CPU",
       "billing" : {
         "code" : "modelarts.vm.cpu.2u",
         "unit_num" : 1
       },
       "flavor_info" : {
         "max_num" : 1,
         "cpu" : {
           "arch" : "x86",
           "core_num" : 2
         },
         "memory" : {
           "size" : 8,
           "unit" : "GB"
         },
         "disk" : {
           "size" : 50,
           "unit" : "GB"
         }
       }
     }, {
       "flavor_id" : "modelarts.vm.cpu.8u",
       "flavor_name" : "Computing CPU(8U) instance",
       "flavor_type" : "CPU",
       "billing" : {
         "code" : "modelarts.vm.cpu.8u",
         "unit_num" : 1
       },
       "flavor_info" : {
         "max_num" : 16,
         "cpu" : {
           "arch" : "x86",
           "core_num" : 8
         },
         "memory" : {
           "size" : 32,
           "unit" : "GB"
         },
         "disk" : {
           "size" : 50,
           "unit" : "GB"
         }
       }
     } ]
   }

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
200         ok
=========== ===========

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
