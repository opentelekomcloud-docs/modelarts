:original_name: PatchNetwork.html

.. _PatchNetwork:

Updating a Network Resource
===========================

Function
--------

This API is used to update a specified network resource.

URI
---

PATCH /v1/{project_id}/networks/{network_name}

.. table:: **Table 1** Path Parameters

   +--------------+-----------+--------+------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                              |
   +==============+===========+========+==========================================================================================+
   | project_id   | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +--------------+-----------+--------+------------------------------------------------------------------------------------------+
   | network_name | Yes       | String | Network resource name.                                                                   |
   +--------------+-----------+--------+------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   ============ ========= ====== ===============================
   Parameter    Mandatory Type   Description
   ============ ========= ====== ===============================
   Content-Type Yes       String Application/merge-patch + JSON.
   ============ ========= ====== ===============================

.. table:: **Table 3** Request body parameters

   +-----------+-----------+---------------------------------------------------------------------------------------------------+---------------------------------------+
   | Parameter | Mandatory | Type                                                                                              | Description                           |
   +===========+===========+===================================================================================================+=======================================+
   | metadata  | No        | :ref:`NetworkMetadataUpdate <en-us_topic_0000002340898494__request_networkmetadataupdate>` object | Updated network resource metadata.    |
   +-----------+-----------+---------------------------------------------------------------------------------------------------+---------------------------------------+
   | spec      | No        | :ref:`NetworkSpecUpdate <en-us_topic_0000002340898494__request_networkspecupdate>` object         | Updated network resource description. |
   +-----------+-----------+---------------------------------------------------------------------------------------------------+---------------------------------------+

.. _en-us_topic_0000002340898494__request_networkmetadataupdate:

.. table:: **Table 4** NetworkMetadataUpdate

   +-------------+-----------+-------------------------------------------------------------------------------------------------------------+-----------------------------+
   | Parameter   | Mandatory | Type                                                                                                        | Description                 |
   +=============+===========+=============================================================================================================+=============================+
   | annotations | No        | :ref:`NetworkMetadataAnnotations <en-us_topic_0000002340898494__request_networkmetadataannotations>` object | Resource annotations.       |
   +-------------+-----------+-------------------------------------------------------------------------------------------------------------+-----------------------------+
   | labels      | No        | :ref:`NetworkUpdateLabels <en-us_topic_0000002340898494__request_networkupdatelabels>` object               | Labels of network resources |
   +-------------+-----------+-------------------------------------------------------------------------------------------------------------+-----------------------------+

.. _en-us_topic_0000002340898494__request_networkmetadataannotations:

.. table:: **Table 5** NetworkMetadataAnnotations

   +--------------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                | Mandatory | Type   | Description                                                                                                                   |
   +==========================+===========+========+===============================================================================================================================+
   | os.modelarts/description | No        | String | Network resource description, which is used to describe a scenario. The following special characters are not allowed: !<>=&"' |
   +--------------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002340898494__request_networkupdatelabels:

.. table:: **Table 6** NetworkUpdateLabels

   +---------------------------+-----------+--------+----------------------------------------------+
   | Parameter                 | Mandatory | Type   | Description                                  |
   +===========================+===========+========+==============================================+
   | os.modelarts/workspace.id | No        | String | ID of the workspace to which network belongs |
   +---------------------------+-----------+--------+----------------------------------------------+

.. _en-us_topic_0000002340898494__request_networkspecupdate:

.. table:: **Table 7** NetworkSpecUpdate

   +------------+-----------+-------------------------------------------------------------------------------------------+----------------------------------------------------------------------+
   | Parameter  | Mandatory | Type                                                                                      | Description                                                          |
   +============+===========+===========================================================================================+======================================================================+
   | ipv6enable | No        | Boolean                                                                                   | Whether to enable IPv6. Once IPv6 is enabled, it cannot be disabled. |
   +------------+-----------+-------------------------------------------------------------------------------------------+----------------------------------------------------------------------+
   | connection | No        | :ref:`NetworkConnection <en-us_topic_0000002340898494__request_networkconnection>` object | Updated network connection.                                          |
   +------------+-----------+-------------------------------------------------------------------------------------------+----------------------------------------------------------------------+

.. _en-us_topic_0000002340898494__request_networkconnection:

.. table:: **Table 8** NetworkConnection

   +------------------------+-----------+---------------------------------------------------------------------------------------------------------------+---------------------------------------------+
   | Parameter              | Mandatory | Type                                                                                                          | Description                                 |
   +========================+===========+===============================================================================================================+=============================================+
   | peerConnectionList     | No        | Array of :ref:`PeerConnectionItem <en-us_topic_0000002340898494__request_peerconnectionitem>` objects         | Peering connections                         |
   +------------------------+-----------+---------------------------------------------------------------------------------------------------------------+---------------------------------------------+
   | sfsTurboConnectionList | No        | Array of :ref:`SfsTurboConnectionItem <en-us_topic_0000002340898494__request_sfsturboconnectionitem>` objects | SFS Turbo connections through attached NICs |
   +------------------------+-----------+---------------------------------------------------------------------------------------------------------------+---------------------------------------------+

.. _en-us_topic_0000002340898494__request_peerconnectionitem:

.. table:: **Table 9** PeerConnectionItem

   +----------------+-----------+---------+--------------------------------------------------------------------+
   | Parameter      | Mandatory | Type    | Description                                                        |
   +================+===========+=========+====================================================================+
   | peerVpcId      | Yes       | String  | VPC ID of the peer end.                                            |
   +----------------+-----------+---------+--------------------------------------------------------------------+
   | peerSubnetId   | Yes       | String  | Subnet ID of the peer end.                                         |
   +----------------+-----------+---------+--------------------------------------------------------------------+
   | defaultGateWay | No        | Boolean | Whether to create a default route. The default value is **false**. |
   +----------------+-----------+---------+--------------------------------------------------------------------+

.. _en-us_topic_0000002340898494__request_sfsturboconnectionitem:

.. table:: **Table 10** SfsTurboConnectionItem

   ========= ========= ====== ==============================
   Parameter Mandatory Type   Description
   ========= ========= ====== ==============================
   name      Yes       String Name of an SFS Turbo instance.
   sfsId     Yes       String ID of an SFS Turbo instance.
   ========= ========= ====== ==============================

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 11** Response body parameters

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
   | metadata              | :ref:`NetworkMetadata <en-us_topic_0000002340898494__response_networkmetadata>` object | Metadata of network resources.    |
   +-----------------------+----------------------------------------------------------------------------------------+-----------------------------------+
   | spec                  | :ref:`NetworkSpec <en-us_topic_0000002340898494__response_networkspec>` object         | Description of network resources. |
   +-----------------------+----------------------------------------------------------------------------------------+-----------------------------------+
   | status                | :ref:`NetworkStatus <en-us_topic_0000002340898494__response_networkstatus>` object     | Status of network resources.      |
   +-----------------------+----------------------------------------------------------------------------------------+-----------------------------------+

.. _en-us_topic_0000002340898494__response_networkmetadata:

.. table:: **Table 12** NetworkMetadata

   +-------------------+--------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | Parameter         | Type                                                                                                         | Description                                                                 |
   +===================+==============================================================================================================+=============================================================================+
   | name              | String                                                                                                       | Automatically generated network name, which is equivalent to **networkId**. |
   +-------------------+--------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | creationTimestamp | String                                                                                                       | Timestamp, for example, **2021-11-01T03:49:41Z**.                           |
   +-------------------+--------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | labels            | :ref:`NetworkMetadataLabels <en-us_topic_0000002340898494__response_networkmetadatalabels>` object           | Labels of network resources.                                                |
   +-------------------+--------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | annotations       | :ref:`NetworkMetadataAnnotations <en-us_topic_0000002340898494__response_networkmetadataannotations>` object | Annotations of network resources.                                           |
   +-------------------+--------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+

.. _en-us_topic_0000002340898494__response_networkmetadatalabels:

.. table:: **Table 13** NetworkMetadataLabels

   +---------------------------+--------+-------------------------------------------+
   | Parameter                 | Type   | Description                               |
   +===========================+========+===========================================+
   | os.modelarts/name         | String | Specified network name.                   |
   +---------------------------+--------+-------------------------------------------+
   | os.modelarts/workspace.id | String | Workspace ID. The default value is **0**. |
   +---------------------------+--------+-------------------------------------------+

.. _en-us_topic_0000002340898494__response_networkmetadataannotations:

.. table:: **Table 14** NetworkMetadataAnnotations

   +--------------------------+--------+-------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                | Type   | Description                                                                                                                   |
   +==========================+========+===============================================================================================================================+
   | os.modelarts/description | String | Network resource description, which is used to describe a scenario. The following special characters are not allowed: !<>=&"' |
   +--------------------------+--------+-------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002340898494__response_networkspec:

.. table:: **Table 15** NetworkSpec

   +------------+--------------------------------------------------------------------------------------------+----------------------------------------------------------------------+
   | Parameter  | Type                                                                                       | Description                                                          |
   +============+============================================================================================+======================================================================+
   | ipv6enable | Boolean                                                                                    | Whether to enable IPv6. Once IPv6 is enabled, it cannot be disabled. |
   +------------+--------------------------------------------------------------------------------------------+----------------------------------------------------------------------+
   | cidr       | String                                                                                     | Network CIDR.                                                        |
   +------------+--------------------------------------------------------------------------------------------+----------------------------------------------------------------------+
   | connection | :ref:`NetworkConnection <en-us_topic_0000002340898494__response_networkconnection>` object | Automatically interconnected endpoint.                               |
   +------------+--------------------------------------------------------------------------------------------+----------------------------------------------------------------------+

.. _en-us_topic_0000002340898494__response_networkconnection:

.. table:: **Table 16** NetworkConnection

   +------------------------+----------------------------------------------------------------------------------------------------------------+---------------------------------------------+
   | Parameter              | Type                                                                                                           | Description                                 |
   +========================+================================================================================================================+=============================================+
   | peerConnectionList     | Array of :ref:`PeerConnectionItem <en-us_topic_0000002340898494__response_peerconnectionitem>` objects         | Peering connections                         |
   +------------------------+----------------------------------------------------------------------------------------------------------------+---------------------------------------------+
   | sfsTurboConnectionList | Array of :ref:`SfsTurboConnectionItem <en-us_topic_0000002340898494__response_sfsturboconnectionitem>` objects | SFS Turbo connections through attached NICs |
   +------------------------+----------------------------------------------------------------------------------------------------------------+---------------------------------------------+

.. _en-us_topic_0000002340898494__response_peerconnectionitem:

.. table:: **Table 17** PeerConnectionItem

   +----------------+---------+--------------------------------------------------------------------+
   | Parameter      | Type    | Description                                                        |
   +================+=========+====================================================================+
   | peerVpcId      | String  | VPC ID of the peer end.                                            |
   +----------------+---------+--------------------------------------------------------------------+
   | peerSubnetId   | String  | Subnet ID of the peer end.                                         |
   +----------------+---------+--------------------------------------------------------------------+
   | defaultGateWay | Boolean | Whether to create a default route. The default value is **false**. |
   +----------------+---------+--------------------------------------------------------------------+

.. _en-us_topic_0000002340898494__response_sfsturboconnectionitem:

.. table:: **Table 18** SfsTurboConnectionItem

   ========= ====== ==============================
   Parameter Type   Description
   ========= ====== ==============================
   name      String Name of an SFS Turbo instance.
   sfsId     String ID of an SFS Turbo instance.
   ========= ====== ==============================

.. _en-us_topic_0000002340898494__response_networkstatus:

.. table:: **Table 19** NetworkStatus

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
   | connectionStatus      | :ref:`NetworkConnectionStatus <en-us_topic_0000002340898494__response_networkconnectionstatus>` object | Network connection status.                     |
   +-----------------------+--------------------------------------------------------------------------------------------------------+------------------------------------------------+

.. _en-us_topic_0000002340898494__response_networkconnectionstatus:

.. table:: **Table 20** NetworkConnectionStatus

   +----------------------+--------------------------------------------------------------------------------------------------------------------+-----------------------------------------------+
   | Parameter            | Type                                                                                                               | Description                                   |
   +======================+====================================================================================================================+===============================================+
   | peerConnectionStatus | Array of :ref:`PeerConnectionStatus <en-us_topic_0000002340898494__response_peerconnectionstatus>` objects         | Peering connection status                     |
   +----------------------+--------------------------------------------------------------------------------------------------------------------+-----------------------------------------------+
   | sfsTurboStatus       | Array of :ref:`SfsTurboConnectionStatus <en-us_topic_0000002340898494__response_sfsturboconnectionstatus>` objects | Status of SFS Turbo accessible to the network |
   +----------------------+--------------------------------------------------------------------------------------------------------------------+-----------------------------------------------+

.. _en-us_topic_0000002340898494__response_peerconnectionstatus:

.. table:: **Table 21** PeerConnectionStatus

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

.. _en-us_topic_0000002340898494__response_sfsturboconnectionstatus:

.. table:: **Table 22** SfsTurboConnectionStatus

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

**Status code: 400**

.. table:: **Table 23** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 404**

.. table:: **Table 24** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

-  Interconnect with a VPC.

   .. code-block::

      PATCH https://{endpoint}/v1/{project_id}/networks/{network_name}

      {
        "spec" : {
          "connection" : {
            "peerConnectionList" : [ {
              "peerVpcId" : "359668f4-fbef-4404-b9bc-781142518d3b",
              "peerSubnetId" : "8f21dbea-df13-4669-8a17-0efba195997b",
              "defaultGateWay" : false
            } ]
          }
        }
      }

-  Associate SFS Turbo.

   .. code-block::

      PATCH https://{endpoint}/v1/{project_id}/networks/{network_name}

      {
        "spec" : {
          "connection" : {
            "sfsTurboConnectionList" : [ {
              "sfsId" : "2a220ce2-936c-4041-8478-c731bf934b11",
              "name" : "sfs-turbo-a066-bbb"
            } ]
          }
        }
      }

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
       "connection" : {
         "peerConnectionList" : [ {
           "peerVpcId" : "03e4f4d7-fc62-409b-9c52-df885525e30b",
           "peerSubnetId" : "42aeebc3-f7c7-45aa-b884-e6e9ac2f841d"
         } ],
         "sfsTurboConnectionList" : [ {
           "sfsId" : "97beb2bb-1a5b-41dd-b7fb-65a9c7954517",
           "name" : "mulVpc-02"
         } ]
       }
     },
     "status" : {
       "phase" : "Active",
       "connectionStatus" : { }
     }
   }

**Status code: 400**

Bad request

.. code-block::

   {
     "error_code" : "ModelArts.50004000",
     "error_msg" : "Bad request."
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
400         Bad request
404         Not found.
=========== ===========

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
