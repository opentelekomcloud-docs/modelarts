:original_name: ListPoolNodes.html

.. _ListPoolNodes:

Obtaining Nodes
===============

Function
--------

This API is used to obtain nodes in a resource pool.

URI
---

GET /v2/{project_id}/pools/{pool_name}/nodes

.. table:: **Table 1** Path Parameters

   ========== ========= ====== ========================
   Parameter  Mandatory Type   Description
   ========== ========= ====== ========================
   project_id Yes       String Project ID.
   pool_name  Yes       String Name of a resource pool.
   ========== ========= ====== ========================

.. table:: **Table 2** Query Parameters

   +-----------+-----------+---------+-----------------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                               |
   +===========+===========+=========+===========================================================+
   | continue  | No        | String  | Previous query location in pagination query.              |
   +-----------+-----------+---------+-----------------------------------------------------------+
   | limit     | No        | Integer | Number of records returned for a single pagination query. |
   +-----------+-----------+---------+-----------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------------------+------------------------------------------------------------------------------------------+-------------------------+
   | Parameter             | Type                                                                                     | Description             |
   +=======================+==========================================================================================+=========================+
   | apiVersion            | String                                                                                   | API version. Options:   |
   |                       |                                                                                          |                         |
   |                       |                                                                                          | -  **v2**               |
   +-----------------------+------------------------------------------------------------------------------------------+-------------------------+
   | kind                  | String                                                                                   | Resource type. Options: |
   |                       |                                                                                          |                         |
   |                       |                                                                                          | -  **NodeList**: nodes  |
   +-----------------------+------------------------------------------------------------------------------------------+-------------------------+
   | metadata              | :ref:`NodeListMetadata <en-us_topic_0000002044216596__response_nodelistmetadata>` object | Metadata of resources.  |
   +-----------------------+------------------------------------------------------------------------------------------+-------------------------+
   | items                 | Array of :ref:`Node <en-us_topic_0000002044216596__response_node>` objects               | Nodes.                  |
   +-----------------------+------------------------------------------------------------------------------------------+-------------------------+

.. _en-us_topic_0000002044216596__response_nodelistmetadata:

.. table:: **Table 4** NodeListMetadata

   ================== ====== =======================================
   Parameter          Type   Description
   ================== ====== =======================================
   continue           String Next query position in pagination query
   remainingItemCount Long   Remaining resources
   ================== ====== =======================================

.. _en-us_topic_0000002044216596__response_node:

.. table:: **Table 5** Node

   +-----------------------+------------------------------------------------------------------------------+-------------------------+
   | Parameter             | Type                                                                         | Description             |
   +=======================+==============================================================================+=========================+
   | apiVersion            | String                                                                       | API version. Options:   |
   |                       |                                                                              |                         |
   |                       |                                                                              | -  **v2**               |
   +-----------------------+------------------------------------------------------------------------------+-------------------------+
   | kind                  | String                                                                       | Resource type. Options: |
   |                       |                                                                              |                         |
   |                       |                                                                              | -  **Node**: node       |
   +-----------------------+------------------------------------------------------------------------------+-------------------------+
   | metadata              | :ref:`metadata <en-us_topic_0000002044216596__response_metadata>` object     | Basic node information. |
   +-----------------------+------------------------------------------------------------------------------+-------------------------+
   | spec                  | :ref:`NodeSpec <en-us_topic_0000002044216596__response_nodespec>` object     | Node description.       |
   +-----------------------+------------------------------------------------------------------------------+-------------------------+
   | status                | :ref:`NodeStatus <en-us_topic_0000002044216596__response_nodestatus>` object | Node status.            |
   +-----------------------+------------------------------------------------------------------------------+-------------------------+

.. _en-us_topic_0000002044216596__response_metadata:

.. table:: **Table 6** metadata

   +-------------------+------------------------------------------------------------------------------+-----------------------------+
   | Parameter         | Type                                                                         | Description                 |
   +===================+==============================================================================+=============================+
   | name              | String                                                                       | Node name.                  |
   +-------------------+------------------------------------------------------------------------------+-----------------------------+
   | creationTimestamp | String                                                                       | Creation time.              |
   +-------------------+------------------------------------------------------------------------------+-----------------------------+
   | labels            | :ref:`NodeLabels <en-us_topic_0000002044216596__response_nodelabels>` object | Label information of a node |
   +-------------------+------------------------------------------------------------------------------+-----------------------------+

.. _en-us_topic_0000002044216596__response_nodelabels:

.. table:: **Table 7** NodeLabels

   +---------------------------------+--------+-----------------------------------------------+
   | Parameter                       | Type   | Description                                   |
   +=================================+========+===============================================+
   | os.modelarts.node/cluster       | String | Name of the cluster where the node is located |
   +---------------------------------+--------+-----------------------------------------------+
   | os.modelarts.node/elastic.quota | String | Logical pool of the node                      |
   +---------------------------------+--------+-----------------------------------------------+
   | os.modelarts.node/nodepool      | String | Name of the pool where the node is located    |
   +---------------------------------+--------+-----------------------------------------------+

.. _en-us_topic_0000002044216596__response_nodespec:

.. table:: **Table 8** NodeSpec

   +-------------+--------------------------------------------------------------------------------+--------------------------+
   | Parameter   | Type                                                                           | Description              |
   +=============+================================================================================+==========================+
   | flavor      | String                                                                         | Node specifications      |
   +-------------+--------------------------------------------------------------------------------+--------------------------+
   | hostNetwork | :ref:`NodeNetwork <en-us_topic_0000002044216596__response_nodenetwork>` object | Node network information |
   +-------------+--------------------------------------------------------------------------------+--------------------------+

.. _en-us_topic_0000002044216596__response_nodenetwork:

.. table:: **Table 9** NodeNetwork

   ============== ================ ==================
   Parameter      Type             Description
   ============== ================ ==================
   vpc            String           VPC ID
   subnet         String           Subnet ID
   securityGroups Array of strings Security group IDs
   ============== ================ ==================

.. _en-us_topic_0000002044216596__response_nodestatus:

.. table:: **Table 10** NodeStatus

   +-----------------------+----------------------------------------------------------------------------------+----------------------------------------------------+
   | Parameter             | Type                                                                             | Description                                        |
   +=======================+==================================================================================+====================================================+
   | phase                 | String                                                                           | Node status. Options:                              |
   |                       |                                                                                  |                                                    |
   |                       |                                                                                  | -  **Available**: The node is available.           |
   |                       |                                                                                  |                                                    |
   |                       |                                                                                  | -  **Creating**: The node is being created.        |
   |                       |                                                                                  |                                                    |
   |                       |                                                                                  | -  **Deleting**: The node is being deleted.        |
   |                       |                                                                                  |                                                    |
   |                       |                                                                                  | -  **Abnormal**: The node is not running properly. |
   +-----------------------+----------------------------------------------------------------------------------+----------------------------------------------------+
   | az                    | String                                                                           | AZ to which the node belongs                       |
   +-----------------------+----------------------------------------------------------------------------------+----------------------------------------------------+
   | privateIp             | String                                                                           | IP address of a node                               |
   +-----------------------+----------------------------------------------------------------------------------+----------------------------------------------------+
   | resources             | :ref:`NodeResource <en-us_topic_0000002044216596__response_noderesource>` object | Node resources                                     |
   +-----------------------+----------------------------------------------------------------------------------+----------------------------------------------------+
   | availableResources    | :ref:`NodeResource <en-us_topic_0000002044216596__response_noderesource>` object | Available node resources                           |
   +-----------------------+----------------------------------------------------------------------------------+----------------------------------------------------+

.. _en-us_topic_0000002044216596__response_noderesource:

.. table:: **Table 11** NodeResource

   ============== ====== ===========
   Parameter      Type   Description
   ============== ====== ===========
   cpu            String CPUs.
   memory         String Memory.
   nvidia.com/gpu String GPUs.
   ============== ====== ===========

**Status code: 404**

.. table:: **Table 12** Response body parameters

   +-----------------------+-----------------------+-----------------------+
   | Parameter             | Type                  | Description           |
   +=======================+=======================+=======================+
   | error_code            | String                | Error code.           |
   |                       |                       |                       |
   |                       |                       | Minimum: **8**        |
   |                       |                       |                       |
   |                       |                       | Maximum: **36**       |
   +-----------------------+-----------------------+-----------------------+
   | error_msg             | String                | Error message.        |
   |                       |                       |                       |
   |                       |                       | Minimum: **2**        |
   |                       |                       |                       |
   |                       |                       | Maximum: **512**      |
   +-----------------------+-----------------------+-----------------------+

Example Requests
----------------

Obtain nodes in a resource pool.

.. code-block:: text

   GET https://{endpoint}/v2/{project_id}/pools/{pool_name}/nodes

   { }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "kind" : "NodeList",
     "apiVersion" : "v2",
     "metadata" : { },
     "items" : [ {
       "kind" : "Node",
       "apiVersion" : "v2",
       "metadata" : {
         "name" : "os-node-created-zlncn",
         "creationTimestamp" : "2022-09-16T05:32:44Z"
       },
       "spec" : {
         "flavor" : "modelarts.vm.cpu.4ud"
       },
       "status" : {
         "phase" : "Available",
         "az" : "xx-xxxx-xx",
         "privateIp" : "192.168.0.1",
         "resources" : {
           "cpu" : "3920m",
           "memory" : "6270Mi"
         },
         "availableResources" : {
           "cpu" : "2970m",
           "memory" : "4558Mi"
         }
       }
     }, {
       "kind" : "Node",
       "apiVersion" : "v2",
       "metadata" : {
         "name" : "os-node-created-4s522",
         "creationTimestamp" : "2022-09-16T03:20:53Z"
       },
       "spec" : {
         "flavor" : "modelarts.vm.cpu.4ud"
       },
       "status" : {
         "phase" : "Available",
         "az" : "xx-xxxx-xx",
         "privateIp" : "192.168.0.2",
         "resources" : {
           "cpu" : "3920m",
           "memory" : "6270Mi"
         },
         "availableResources" : {
           "cpu" : "2970m",
           "memory" : "4558Mi"
         }
       }
     }, {
       "kind" : "Node",
       "apiVersion" : "v2",
       "metadata" : {
         "name" : "os-node-created-v7hfj",
         "creationTimestamp" : "2022-09-16T09:16:37Z"
       },
       "spec" : {
         "flavor" : "modelarts.vm.cpu.4ud"
       },
       "status" : {
         "phase" : "Available",
         "az" : "xx-xxxx-xx",
         "privateIp" : "192.168.0.3",
         "resources" : {
           "cpu" : "3920m",
           "memory" : "6270Mi"
         },
         "availableResources" : {
           "cpu" : "3720m",
           "memory" : "5670Mi"
         }
       }
     } ]
   }

**Status code: 404**

Not found.

.. code-block::

   {
     "error_code" : "ModelArts.50015001",
     "error_msg" : "pool not found"
   }

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
200         OK
404         Not found.
=========== ===========

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
