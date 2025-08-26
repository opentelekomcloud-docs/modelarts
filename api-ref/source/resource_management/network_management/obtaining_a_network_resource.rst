:original_name: ShowNetwork.html

.. _ShowNetwork:

Obtaining a Network Resource
============================

Function
--------

This API is used to obtain details about a specified network resource.

URI
---

GET /v1/{project_id}/networks/{network_name}

.. table:: **Table 1** Path Parameters

   +--------------+-----------+--------+------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                              |
   +==============+===========+========+==========================================================================================+
   | project_id   | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +--------------+-----------+--------+------------------------------------------------------------------------------------------+
   | network_name | Yes       | String | Automatically generated network name.                                                    |
   +--------------+-----------+--------+------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   +-----------------------+----------------------------------------------------------------------------------------+-----------------------------------+
   | Parameter             | Type                                                                                   | Description                       |
   +=======================+========================================================================================+===================================+
   | apiVersion            | String                                                                                 | API version. Options:             |
   |                       |                                                                                        |                                   |
   |                       |                                                                                        | -  **v1**                         |
   +-----------------------+----------------------------------------------------------------------------------------+-----------------------------------+
   | kind                  | String                                                                                 | Resource type. Options:           |
   |                       |                                                                                        |                                   |
   |                       |                                                                                        | -  **Network**                    |
   +-----------------------+----------------------------------------------------------------------------------------+-----------------------------------+
   | metadata              | :ref:`NetworkMetadata <en-us_topic_0000002374896561__response_networkmetadata>` object | Metadata of network resources.    |
   +-----------------------+----------------------------------------------------------------------------------------+-----------------------------------+
   | spec                  | :ref:`NetworkSpec <en-us_topic_0000002374896561__response_networkspec>` object         | Description of network resources. |
   +-----------------------+----------------------------------------------------------------------------------------+-----------------------------------+
   | status                | :ref:`NetworkStatus <en-us_topic_0000002374896561__response_networkstatus>` object     | Status of network resources.      |
   +-----------------------+----------------------------------------------------------------------------------------+-----------------------------------+

.. _en-us_topic_0000002374896561__response_networkmetadata:

.. table:: **Table 3** NetworkMetadata

   +-------------------+--------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | Parameter         | Type                                                                                                         | Description                                                                 |
   +===================+==============================================================================================================+=============================================================================+
   | name              | String                                                                                                       | Automatically generated network name, which is equivalent to **networkId**. |
   +-------------------+--------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | creationTimestamp | String                                                                                                       | Timestamp, for example, **2021-11-01T03:49:41Z**.                           |
   +-------------------+--------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | labels            | :ref:`NetworkMetadataLabels <en-us_topic_0000002374896561__response_networkmetadatalabels>` object           | Labels of network resources.                                                |
   +-------------------+--------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | annotations       | :ref:`NetworkMetadataAnnotations <en-us_topic_0000002374896561__response_networkmetadataannotations>` object | Annotations of network resources.                                           |
   +-------------------+--------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+

.. _en-us_topic_0000002374896561__response_networkmetadatalabels:

.. table:: **Table 4** NetworkMetadataLabels

   +---------------------------+--------+-------------------------------------------+
   | Parameter                 | Type   | Description                               |
   +===========================+========+===========================================+
   | os.modelarts/name         | String | Specified network name.                   |
   +---------------------------+--------+-------------------------------------------+
   | os.modelarts/workspace.id | String | Workspace ID. The default value is **0**. |
   +---------------------------+--------+-------------------------------------------+

.. _en-us_topic_0000002374896561__response_networkmetadataannotations:

.. table:: **Table 5** NetworkMetadataAnnotations

   +--------------------------+--------+-------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                | Type   | Description                                                                                                                   |
   +==========================+========+===============================================================================================================================+
   | os.modelarts/description | String | Network resource description, which is used to describe a scenario. The following special characters are not allowed: !<>=&"' |
   +--------------------------+--------+-------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002374896561__response_networkspec:

.. table:: **Table 6** NetworkSpec

   +------------+--------------------------------------------------------------------------------------------+----------------------------------------------------------------------+
   | Parameter  | Type                                                                                       | Description                                                          |
   +============+============================================================================================+======================================================================+
   | ipv6enable | Boolean                                                                                    | Whether to enable IPv6. Once IPv6 is enabled, it cannot be disabled. |
   +------------+--------------------------------------------------------------------------------------------+----------------------------------------------------------------------+
   | cidr       | String                                                                                     | Network CIDR.                                                        |
   +------------+--------------------------------------------------------------------------------------------+----------------------------------------------------------------------+
   | connection | :ref:`NetworkConnection <en-us_topic_0000002374896561__response_networkconnection>` object | Automatically interconnected endpoint.                               |
   +------------+--------------------------------------------------------------------------------------------+----------------------------------------------------------------------+

.. _en-us_topic_0000002374896561__response_networkconnection:

.. table:: **Table 7** NetworkConnection

   +------------------------+----------------------------------------------------------------------------------------------------------------+---------------------------------------------+
   | Parameter              | Type                                                                                                           | Description                                 |
   +========================+================================================================================================================+=============================================+
   | peerConnectionList     | Array of :ref:`PeerConnectionItem <en-us_topic_0000002374896561__response_peerconnectionitem>` objects         | Peering connections                         |
   +------------------------+----------------------------------------------------------------------------------------------------------------+---------------------------------------------+
   | sfsTurboConnectionList | Array of :ref:`SfsTurboConnectionItem <en-us_topic_0000002374896561__response_sfsturboconnectionitem>` objects | SFS Turbo connections through attached NICs |
   +------------------------+----------------------------------------------------------------------------------------------------------------+---------------------------------------------+

.. _en-us_topic_0000002374896561__response_peerconnectionitem:

.. table:: **Table 8** PeerConnectionItem

   +----------------+---------+--------------------------------------------------------------------+
   | Parameter      | Type    | Description                                                        |
   +================+=========+====================================================================+
   | peerVpcId      | String  | VPC ID of the peer end.                                            |
   +----------------+---------+--------------------------------------------------------------------+
   | peerSubnetId   | String  | Subnet ID of the peer end.                                         |
   +----------------+---------+--------------------------------------------------------------------+
   | defaultGateWay | Boolean | Whether to create a default route. The default value is **false**. |
   +----------------+---------+--------------------------------------------------------------------+

.. _en-us_topic_0000002374896561__response_sfsturboconnectionitem:

.. table:: **Table 9** SfsTurboConnectionItem

   ========= ====== ==============================
   Parameter Type   Description
   ========= ====== ==============================
   name      String Name of an SFS Turbo instance.
   sfsId     String ID of an SFS Turbo instance.
   ========= ====== ==============================

.. _en-us_topic_0000002374896561__response_networkstatus:

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
   | connectionStatus      | :ref:`NetworkConnectionStatus <en-us_topic_0000002374896561__response_networkconnectionstatus>` object | Network connection status.                     |
   +-----------------------+--------------------------------------------------------------------------------------------------------+------------------------------------------------+

.. _en-us_topic_0000002374896561__response_networkconnectionstatus:

.. table:: **Table 11** NetworkConnectionStatus

   +----------------------+--------------------------------------------------------------------------------------------------------------------+-----------------------------------------------+
   | Parameter            | Type                                                                                                               | Description                                   |
   +======================+====================================================================================================================+===============================================+
   | peerConnectionStatus | Array of :ref:`PeerConnectionStatus <en-us_topic_0000002374896561__response_peerconnectionstatus>` objects         | Peering connection status                     |
   +----------------------+--------------------------------------------------------------------------------------------------------------------+-----------------------------------------------+
   | sfsTurboStatus       | Array of :ref:`SfsTurboConnectionStatus <en-us_topic_0000002374896561__response_sfsturboconnectionstatus>` objects | Status of SFS Turbo accessible to the network |
   +----------------------+--------------------------------------------------------------------------------------------------------------------+-----------------------------------------------+

.. _en-us_topic_0000002374896561__response_peerconnectionstatus:

.. table:: **Table 12** PeerConnectionStatus

   +-----------------------+-----------------------+--------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                        |
   +=======================+=======================+====================================================================+
   | peerVpcId             | String                | VPC ID of the peer end.                                            |
   +-----------------------+-----------------------+--------------------------------------------------------------------+
   | peerSubnetId          | String                | Subnet ID of the peer end.                                         |
   +-----------------------+-----------------------+--------------------------------------------------------------------+
   | defaultGateWay        | Boolean               | Whether to create a default route. The default value is **false**. |
   +-----------------------+-----------------------+--------------------------------------------------------------------+
   | phase                 | String                | Network connection status. The options are as follows:             |
   |                       |                       |                                                                    |
   |                       |                       | -  **Connecting**: The network is being connected.                 |
   |                       |                       |                                                                    |
   |                       |                       | -  **Active**: The network is connected properly.                  |
   |                       |                       |                                                                    |
   |                       |                       | -  **Abnormal**: The network connection is abnormal.               |
   +-----------------------+-----------------------+--------------------------------------------------------------------+

.. _en-us_topic_0000002374896561__response_sfsturboconnectionstatus:

.. table:: **Table 13** SfsTurboConnectionStatus

   +-----------------------+-----------------------+--------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                        |
   +=======================+=======================+====================================================================+
   | name                  | String                | Name of an SFS Turbo instance.                                     |
   +-----------------------+-----------------------+--------------------------------------------------------------------+
   | sfsId                 | String                | ID of an SFS Turbo instance.                                       |
   +-----------------------+-----------------------+--------------------------------------------------------------------+
   | connectionType        | String                | Connection type. The options are as follows:                       |
   |                       |                       |                                                                    |
   |                       |                       | -  **VpcPort**: passthrough through attached NICs                  |
   |                       |                       |                                                                    |
   |                       |                       | -  **Peering**: connection through VPC peering                     |
   +-----------------------+-----------------------+--------------------------------------------------------------------+
   | ipAddr                | String                | SFS Turbo access address.                                          |
   +-----------------------+-----------------------+--------------------------------------------------------------------+
   | status                | String                | Status of the connection to SFS Turbo. The options are as follows: |
   |                       |                       |                                                                    |
   |                       |                       | -  **Active**: The SFS connection is normal.                       |
   |                       |                       |                                                                    |
   |                       |                       | -  **Abnormal**: The SFS connection is abnormal.                   |
   |                       |                       |                                                                    |
   |                       |                       | -  **Creating**: The SFS connection is being set up.               |
   |                       |                       |                                                                    |
   |                       |                       | -  **Deleting**: The SFS connection is being deleted.              |
   +-----------------------+-----------------------+--------------------------------------------------------------------+

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

Obtain details about a network.

.. code-block:: text

   GET https://{endpoint}/v1/{project_id}/networks/{network_name}

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
       "labels" : {
         "os.modelarts/name" : "network-7a03"
       },
       "annotations" : { }
     },
     "spec" : {
       "cidr" : "192.168.128.0/17",
       "connection" : { }
     },
     "status" : {
       "phase" : "Active",
       "connectionStatus" : { }
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
