:original_name: DeleteNetwork.html

.. _DeleteNetwork:

Deleting a Network Resource
===========================

Function
--------

This API is used to delete a specified network resource.

URI
---

DELETE /v1/{project_id}/networks/{network_name}

.. table:: **Table 1** Path Parameters

   ============ ========= ====== ======================
   Parameter    Mandatory Type   Description
   ============ ========= ====== ======================
   project_id   Yes       String Project ID.
   network_name Yes       String Network resource name.
   ============ ========= ====== ======================

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   +-----------------------+--------------------------------------------------------------------------------------+-----------------------------------+
   | Parameter             | Type                                                                                 | Description                       |
   +=======================+======================================================================================+===================================+
   | apiVersion            | String                                                                               | API version. Options:             |
   |                       |                                                                                      |                                   |
   |                       |                                                                                      | -  **v1**                         |
   +-----------------------+--------------------------------------------------------------------------------------+-----------------------------------+
   | kind                  | String                                                                               | Resource type. Options:           |
   |                       |                                                                                      |                                   |
   |                       |                                                                                      | -  **Network**                    |
   +-----------------------+--------------------------------------------------------------------------------------+-----------------------------------+
   | metadata              | :ref:`NeworkMetadata <en-us_topic_0000002080295937__response_neworkmetadata>` object | Metadata of network resources.    |
   +-----------------------+--------------------------------------------------------------------------------------+-----------------------------------+
   | spec                  | :ref:`NetworkSpec <en-us_topic_0000002080295937__response_networkspec>` object       | Description of network resources. |
   +-----------------------+--------------------------------------------------------------------------------------+-----------------------------------+
   | status                | :ref:`NetworkStatus <en-us_topic_0000002080295937__response_networkstatus>` object   | Status of network resources.      |
   +-----------------------+--------------------------------------------------------------------------------------+-----------------------------------+

.. _en-us_topic_0000002080295937__response_neworkmetadata:

.. table:: **Table 3** NeworkMetadata

   +-------------------+--------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | Parameter         | Type                                                                                                         | Description                                                                 |
   +===================+==============================================================================================================+=============================================================================+
   | name              | String                                                                                                       | Automatically generated network name, which is equivalent to **networkId**. |
   +-------------------+--------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | creationTimestamp | String                                                                                                       | Timestamp, for example, 2021-11-01T03:49:41Z.                               |
   +-------------------+--------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | labels            | :ref:`NetworkMetadataLabels <en-us_topic_0000002080295937__response_networkmetadatalabels>` object           | Labels of network resources.                                                |
   +-------------------+--------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | annotations       | :ref:`NetworkMetadataAnnotations <en-us_topic_0000002080295937__response_networkmetadataannotations>` object | Annotations of network resources.                                           |
   +-------------------+--------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+

.. _en-us_topic_0000002080295937__response_networkmetadatalabels:

.. table:: **Table 4** NetworkMetadataLabels

   +-----------------------+-----------------------+-------------------------+
   | Parameter             | Type                  | Description             |
   +=======================+=======================+=========================+
   | os.modelarts/name     | String                | Specified network name. |
   |                       |                       |                         |
   |                       |                       | Minimum: **4**          |
   |                       |                       |                         |
   |                       |                       | Maximum: **32**         |
   +-----------------------+-----------------------+-------------------------+

.. _en-us_topic_0000002080295937__response_networkmetadataannotations:

.. table:: **Table 5** NetworkMetadataAnnotations

   +--------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                | Type                  | Description                                                                                                                   |
   +==========================+=======================+===============================================================================================================================+
   | os.modelarts/description | String                | Network resource description, which is used to describe a scenario. The following special characters are not allowed: !<>=&"' |
   |                          |                       |                                                                                                                               |
   |                          |                       | Minimum: **0**                                                                                                                |
   |                          |                       |                                                                                                                               |
   |                          |                       | Maximum: **100**                                                                                                              |
   +--------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002080295937__response_networkspec:

.. table:: **Table 6** NetworkSpec

   +-----------------------+--------------------------------------------------------------------------------------------+----------------------------------------------------------------------+
   | Parameter             | Type                                                                                       | Description                                                          |
   +=======================+============================================================================================+======================================================================+
   | ipv6enable            | Boolean                                                                                    | Whether to enable IPv6. Once IPv6 is enabled, it cannot be disabled. |
   +-----------------------+--------------------------------------------------------------------------------------------+----------------------------------------------------------------------+
   | cidr                  | String                                                                                     | Network CIDR. Value range:                                           |
   |                       |                                                                                            |                                                                      |
   |                       |                                                                                            | -  172.16.0.0/12-172.16.0.0/24                                       |
   |                       |                                                                                            |                                                                      |
   |                       |                                                                                            | -  192.168.0.0/16-192.168.0.0/24                                     |
   +-----------------------+--------------------------------------------------------------------------------------------+----------------------------------------------------------------------+
   | connection            | :ref:`NetworkConnection <en-us_topic_0000002080295937__response_networkconnection>` object | Automatically interconnected endpoint.                               |
   +-----------------------+--------------------------------------------------------------------------------------------+----------------------------------------------------------------------+

.. _en-us_topic_0000002080295937__response_networkconnection:

.. table:: **Table 7** NetworkConnection

   +------------------------+----------------------------------------------------------------------------------------------------------------+---------------------------------------------+
   | Parameter              | Type                                                                                                           | Description                                 |
   +========================+================================================================================================================+=============================================+
   | peerConnectionList     | Array of :ref:`peerConnectionList <en-us_topic_0000002080295937__response_peerconnectionlist>` objects         | Peering connections                         |
   +------------------------+----------------------------------------------------------------------------------------------------------------+---------------------------------------------+
   | sfsTurboConnectionList | Array of :ref:`sfsTurboConnectionList <en-us_topic_0000002080295937__response_sfsturboconnectionlist>` objects | SFS Turbo connections through attached NICs |
   +------------------------+----------------------------------------------------------------------------------------------------------------+---------------------------------------------+

.. _en-us_topic_0000002080295937__response_peerconnectionlist:

.. table:: **Table 8** peerConnectionList

   +----------------+---------+--------------------------------------------------------------------+
   | Parameter      | Type    | Description                                                        |
   +================+=========+====================================================================+
   | peerVpcId      | String  | VPC ID of the peer end                                             |
   +----------------+---------+--------------------------------------------------------------------+
   | peerSubnetId   | String  | Subnet ID of the peer end                                          |
   +----------------+---------+--------------------------------------------------------------------+
   | defaultGateWay | Boolean | Whether to create a default route. The default value is **false**. |
   +----------------+---------+--------------------------------------------------------------------+

.. _en-us_topic_0000002080295937__response_sfsturboconnectionlist:

.. table:: **Table 9** sfsTurboConnectionList

   ========= ====== =============================
   Parameter Type   Description
   ========= ====== =============================
   sfsId     String ID of an SFS Turbo instance
   name      String Name of an SFS Turbo instance
   ========= ====== =============================

.. _en-us_topic_0000002080295937__response_networkstatus:

.. table:: **Table 10** NetworkStatus

   +-----------------------+--------------------------------------------------------------------------------------------------------+------------------------------------------------+
   | Parameter             | Type                                                                                                   | Description                                    |
   +=======================+========================================================================================================+================================================+
   | phase                 | String                                                                                                 | Current network status. Options:               |
   |                       |                                                                                                        |                                                |
   |                       |                                                                                                        | -  **Creating**: The network is being created. |
   |                       |                                                                                                        |                                                |
   |                       |                                                                                                        | -  **Active**: The network is functional.      |
   |                       |                                                                                                        |                                                |
   |                       |                                                                                                        | -  **Abnormal**: The network malfunctions.     |
   +-----------------------+--------------------------------------------------------------------------------------------------------+------------------------------------------------+
   | connectionStatus      | :ref:`NetworkConnectionStatus <en-us_topic_0000002080295937__response_networkconnectionstatus>` object | Network connection status.                     |
   +-----------------------+--------------------------------------------------------------------------------------------------------+------------------------------------------------+

.. _en-us_topic_0000002080295937__response_networkconnectionstatus:

.. table:: **Table 11** NetworkConnectionStatus

   +----------------------+------------------------------------------------------------------------------------------------------------+-----------------------------------------------+
   | Parameter            | Type                                                                                                       | Description                                   |
   +======================+============================================================================================================+===============================================+
   | peerConnectionStatus | Array of :ref:`peerConnectionStatus <en-us_topic_0000002080295937__response_peerconnectionstatus>` objects | Peering connection status                     |
   +----------------------+------------------------------------------------------------------------------------------------------------+-----------------------------------------------+
   | sfsTurboStatus       | Array of :ref:`sfsTurboStatus <en-us_topic_0000002080295937__response_sfsturbostatus>` objects             | Status of SFS Turbo accessible to the network |
   +----------------------+------------------------------------------------------------------------------------------------------------+-----------------------------------------------+

.. _en-us_topic_0000002080295937__response_peerconnectionstatus:

.. table:: **Table 12** peerConnectionStatus

   +-----------------------+-----------------------+--------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                        |
   +=======================+=======================+====================================================================+
   | peerVpcId             | String                | VPC ID of the peer end                                             |
   +-----------------------+-----------------------+--------------------------------------------------------------------+
   | peerSubnetId          | String                | Subnet ID of the peer end                                          |
   +-----------------------+-----------------------+--------------------------------------------------------------------+
   | defaultGateWay        | Boolean               | Whether to create a default route. The default value is **false**. |
   +-----------------------+-----------------------+--------------------------------------------------------------------+
   | phase                 | String                | Network connection status. Options:                                |
   |                       |                       |                                                                    |
   |                       |                       | -  **Connecting**: The network is being connected.                 |
   |                       |                       |                                                                    |
   |                       |                       | -  **Active**: The network is connected properly.                  |
   |                       |                       |                                                                    |
   |                       |                       | -  **Abnormal**: The network connection is abnormal.               |
   +-----------------------+-----------------------+--------------------------------------------------------------------+

.. _en-us_topic_0000002080295937__response_sfsturbostatus:

.. table:: **Table 13** sfsTurboStatus

   +-----------------------+-----------------------+-------------------------------------------------------+
   | Parameter             | Type                  | Description                                           |
   +=======================+=======================+=======================================================+
   | sfsId                 | String                | SFS Turbo ID                                          |
   +-----------------------+-----------------------+-------------------------------------------------------+
   | name                  | String                | SFS Turbo name                                        |
   +-----------------------+-----------------------+-------------------------------------------------------+
   | status                | String                | Status of the connection to SFS Turbo. Options:       |
   |                       |                       |                                                       |
   |                       |                       | -  **Active**: The SFS connection is normal.          |
   |                       |                       |                                                       |
   |                       |                       | -  **Abnormal**: The SFS connection is abnormal.      |
   |                       |                       |                                                       |
   |                       |                       | -  **Creating**: The SFS connection is being set up.  |
   |                       |                       |                                                       |
   |                       |                       | -  **Deleting**: The SFS connection is being deleted. |
   +-----------------------+-----------------------+-------------------------------------------------------+
   | ipAddr                | String                | SFS Turbo access address                              |
   +-----------------------+-----------------------+-------------------------------------------------------+
   | connectionType        | String                | Connection type. Options:                             |
   |                       |                       |                                                       |
   |                       |                       | -  **VpcPort**: passthrough through attached NICs     |
   |                       |                       |                                                       |
   |                       |                       | -  **Peering**: connection through VPC peering        |
   +-----------------------+-----------------------+-------------------------------------------------------+

**Status code: 404**

.. table:: **Table 14** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Delete a network.

.. code-block:: text

   DELETE https://{endpoint}/v1/{project_id}/networks/{network_name}

   { }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "kind" : "Network",
     "apiVersion" : "v1",
     "metadata" : {
       "name" : "network-7a03-86c13962597848eeb29c5861153a391f",
       "creationTimestamp" : "2022-09-16T09:44:59Z",
       "deletionTimestamp" : "2022-09-16T10:06:27Z",
       "labels" : {
         "os.modelarts/name" : "network-7a03"
       },
       "annotations" : { }
     },
     "spec" : {
       "cidr" : "192.168.128.0/17",
       "connection" : {
         "peerConnectionList" : [ {
           "peerVpcId" : "03e4f4d7-fc62-409b-9c52-df885525e30b",
           "peerSubnetId" : "42aeebc3-f7c7-45aa-b884-e6e9ac2f841d"
         } ]
       }
     },
     "status" : {
       "phase" : "Active",
       "connectionStatus" : {
         "peerConnectionStatus" : [ {
           "peerVpcId" : "03e4f4d7-fc62-409b-9c52-df885525e30b",
           "peerSubnetId" : "42aeebc3-f7c7-45aa-b884-e6e9ac2f841d",
           "phase" : "Active"
         } ]
       }
     }
   }

**Status code: 404**

Not found.

.. code-block::

   {
     "error_code" : "ModelArts.50025001",
     "error_msg" : "Network not exist."
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
