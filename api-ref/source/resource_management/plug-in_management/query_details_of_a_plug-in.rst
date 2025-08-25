:original_name: ShowPlugin.html

.. _ShowPlugin:

Query Details of a Plug-in
==========================

Function
--------

This API is used to query details of a plug-in instance.

URI
---

GET /v2/{project_id}/pools/{pool_name}/plugins/{template_name}

.. table:: **Table 1** Path Parameters

   +---------------+-----------+--------+------------------------------------------------------------------------------------------+
   | Parameter     | Mandatory | Type   | Description                                                                              |
   +===============+===========+========+==========================================================================================+
   | project_id    | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +---------------+-----------+--------+------------------------------------------------------------------------------------------+
   | pool_name     | Yes       | String | Resource pool name.                                                                      |
   +---------------+-----------+--------+------------------------------------------------------------------------------------------+
   | template_name | Yes       | String | Plug-in template name.                                                                   |
   +---------------+-----------+--------+------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------+-----------+--------+------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                    |
   +===========+===========+========+================================================================================================+
   | detail    | No        | String | If this parameter is set to **true**, the resource usage of the plug-in instances is obtained. |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------------------+--------------------------------------------------------------------------------------+-----------------------------------+
   | Parameter             | Type                                                                                 | Description                       |
   +=======================+======================================================================================+===================================+
   | apiVersion            | String                                                                               | API version. Options:             |
   |                       |                                                                                      |                                   |
   |                       |                                                                                      | -  **v2**                         |
   +-----------------------+--------------------------------------------------------------------------------------+-----------------------------------+
   | kind                  | String                                                                               | Type of the plug-in instance.     |
   +-----------------------+--------------------------------------------------------------------------------------+-----------------------------------+
   | metadata              | :ref:`PluginMetadata <en-us_topic_0000002341058310__response_pluginmetadata>` object | Metadata of the plug-in instance. |
   +-----------------------+--------------------------------------------------------------------------------------+-----------------------------------+
   | spec                  | :ref:`PluginSpec <en-us_topic_0000002341058310__response_pluginspec>` object         | Plug-in instance details.         |
   +-----------------------+--------------------------------------------------------------------------------------+-----------------------------------+
   | status                | :ref:`PluginStatus <en-us_topic_0000002341058310__response_pluginstatus>` object     | Plug-in instance status.          |
   +-----------------------+--------------------------------------------------------------------------------------+-----------------------------------+

.. _en-us_topic_0000002341058310__response_pluginmetadata:

.. table:: **Table 4** PluginMetadata

   ================= ====== =============================
   Parameter         Type   Description
   ================= ====== =============================
   name              String Name of the plug-in instance.
   creationTimestamp String Creation time.
   ================= ====== =============================

.. _en-us_topic_0000002341058310__response_pluginspec:

.. table:: **Table 5** PluginSpec

   +-----------+--------------------------------------------------------------------------+------------------------------------------------+
   | Parameter | Type                                                                     | Description                                    |
   +===========+==========================================================================+================================================+
   | template  | :ref:`Template <en-us_topic_0000002341058310__response_template>` object | Template information of the plug-in instances. |
   +-----------+--------------------------------------------------------------------------+------------------------------------------------+

.. _en-us_topic_0000002341058310__response_template:

.. table:: **Table 6** Template

   +-----------+--------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type               | Description                                                                                                                                                                                                                                                                                                                                                         |
   +===========+====================+=====================================================================================================================================================================================================================================================================================================================================================================+
   | name      | String             | Name of the plug-in template to be installed, for example, **log-agent**.                                                                                                                                                                                                                                                                                           |
   +-----------+--------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version   | String             | Version of the plug-in to be installed or upgraded.                                                                                                                                                                                                                                                                                                                 |
   +-----------+--------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | inputs    | Map<String,Object> | Plug-in template installation parameters (varying depending on the plug-in). During the plug-in upgrade, you need to specify all the installation parameters. If the parameters are not specified, the default values in the plug-in template are used. The current plug-in installation parameters can be obtained through the API for querying plug-in instances. |
   +-----------+--------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002341058310__response_pluginstatus:

.. table:: **Table 7** PluginStatus

   +-----------------------+--------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                             | Description                                                                                                                             |
   +=======================+==================================================================================================+=========================================================================================================================================+
   | phase                 | String                                                                                           | Plug-in instance status. Options:                                                                                                       |
   |                       |                                                                                                  |                                                                                                                                         |
   |                       |                                                                                                  | -  **Pending**: The plug-in is being installed.                                                                                         |
   |                       |                                                                                                  |                                                                                                                                         |
   |                       |                                                                                                  | -  **Running**: All of the plug-in instances are running. This specifies that the plug-in runs properly.                                |
   |                       |                                                                                                  |                                                                                                                                         |
   |                       |                                                                                                  | -  **Updating**: The plug-in is being updated.                                                                                          |
   |                       |                                                                                                  |                                                                                                                                         |
   |                       |                                                                                                  | -  **Abnormal**: The plug-in instances are abnormal and the plug-in cannot be used. You can click the status to view the failure cause. |
   |                       |                                                                                                  |                                                                                                                                         |
   |                       |                                                                                                  | -  **Deleting**: The plug-in is being deleted.                                                                                          |
   +-----------------------+--------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | version               | String                                                                                           | Version of the plug-in instances.                                                                                                       |
   +-----------------------+--------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | reason                | String                                                                                           | Details about the plug-in instance installation failure.                                                                                |
   +-----------------------+--------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | values                | String                                                                                           | Installation parameters of the plug-in instances. The parameters vary depending on the plug-in.                                         |
   +-----------------------+--------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | resources             | Array of :ref:`PluginResources <en-us_topic_0000002341058310__response_pluginresources>` objects | Resources used by the plug-in instances.                                                                                                |
   +-----------------------+--------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002341058310__response_pluginresources:

.. table:: **Table 8** PluginResources

   +----------------+----------------------------------------------------------------------------------------+---------------------------------------------+
   | Parameter      | Type                                                                                   | Description                                 |
   +================+========================================================================================+=============================================+
   | involvedObject | :ref:`ObjectReference <en-us_topic_0000002341058310__response_objectreference>` object | Resource objects referenced by the plug-in. |
   +----------------+----------------------------------------------------------------------------------------+---------------------------------------------+
   | replicas       | Integer                                                                                | Number of replicas of the resource object.  |
   +----------------+----------------------------------------------------------------------------------------+---------------------------------------------+
   | limits         | Map<String,String>                                                                     | Limit on requested resources.               |
   +----------------+----------------------------------------------------------------------------------------+---------------------------------------------+
   | requests       | Map<String,String>                                                                     | Requested resources.                        |
   +----------------+----------------------------------------------------------------------------------------+---------------------------------------------+

.. _en-us_topic_0000002341058310__response_objectreference:

.. table:: **Table 9** ObjectReference

   +-----------------+--------+---------------------------------------------------------------------------------+
   | Parameter       | Type   | Description                                                                     |
   +=================+========+=================================================================================+
   | kind            | String | API type of the resource object, for example, **DaemonSet** and **Deployment**. |
   +-----------------+--------+---------------------------------------------------------------------------------+
   | apiVersion      | String | API version of the resource object.                                             |
   +-----------------+--------+---------------------------------------------------------------------------------+
   | namespace       | String | Namespace of the resource object.                                               |
   +-----------------+--------+---------------------------------------------------------------------------------+
   | name            | String | Name of the resource object.                                                    |
   +-----------------+--------+---------------------------------------------------------------------------------+
   | uid             | String | Unique ID of the resource object.                                               |
   +-----------------+--------+---------------------------------------------------------------------------------+
   | resourceVersion | String | Current version of the resource object.                                         |
   +-----------------+--------+---------------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 10** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

This API is used to query details of a plug-in instance.

.. code-block:: text

   GET https://{endpoint}/v2/{project_id}/pools/{pool_name}/plugins/{template_name}?detail=true

   {
     "kind" : "Plugin",
     "apiVersion" : "v2",
     "metadata" : {
       "name" : "pool-6f5da0868084d36f8bd3346036-node-local-dns",
       "creationTimestamp" : "2025-03-17T12:29:18Z"
     },
     "spec" : {
       "template" : {
         "name" : "node-local-dns",
         "version" : "1.6.36",
         "inputs" : {
           "custom" : {
             "enable_dnsconfig_admission" : true,
             "nameserver" : "135.0.0.1",
             "ndots" : "8",
             "search" : "1321"
           },
           "flavor" : {
             "description" : "High avaiable",
             "name" : "HA",
             "resources" : [ {
               "limitsCpu" : "250m",
               "limitsMem" : "512Mi",
               "name" : "node-local-dns-admission-controller",
               "replicas" : 2,
               "requestsCpu" : "250m",
               "requestsMem" : "512Mi"
             }, {
               "limitsCpu" : "500m",
               "limitsMem" : "512Mi",
               "name" : "node-local-dns-cache",
               "requestsCpu" : "25m",
               "requestsMem" : "5Mi"
             } ],
             "size" : "large"
           }
         }
       }
     },
     "status" : {
       "phase" : "Running",
       "version" : "1.6.36",
       "reason" : "Install complete",
       "resources" : [ {
         "limits" : {
           "cpu" : "500m",
           "memory" : "512Mi"
         },
         "requests" : {
           "cpu" : "25m",
           "memory" : "5Mi"
         },
         "involvedObject" : {
           "kind" : "DaemonSet",
           "namespace" : "kube-system",
           "name" : "node-local-dns",
           "uid" : "755437e4-b591-406c-a512-f9a02794082b",
           "apiVersion" : "apps/v1",
           "resourceVersion" : "702874"
         }
       }, {
         "limits" : {
           "cpu" : "250m",
           "memory" : "512Mi"
         },
         "requests" : {
           "cpu" : "250m",
           "memory" : "512Mi"
         },
         "involvedObject" : {
           "kind" : "Deployment",
           "namespace" : "kube-system",
           "name" : "node-local-dns-admission-controller",
           "uid" : "a770edcf-15c2-4caa-b10e-344de7eea7e1",
           "apiVersion" : "apps/v1",
           "resourceVersion" : "705195"
         },
         "replicas" : 2
       } ]
     }
   }

Example Responses
-----------------

**Status code: 200**

Request succeeded.

.. code-block::

   {
     "kind" : "Plugin",
     "apiVersion" : "v2",
     "metadata" : {
       "name" : "pool-6f5da0868084d36f8bd3346036-node-local-dns",
       "creationTimestamp" : "2025-03-17T12:29:18Z"
     },
     "spec" : {
       "template" : {
         "name" : "node-local-dns",
         "version" : "1.6.36",
         "inputs" : {
           "custom" : {
             "enable_dnsconfig_admission" : true,
             "nameserver" : "135.0.0.1",
             "ndots" : "8",
             "search" : "1321"
           },
           "flavor" : {
             "description" : "High avaiable",
             "name" : "HA",
             "resources" : [ {
               "limitsCpu" : "250m",
               "limitsMem" : "512Mi",
               "name" : "node-local-dns-admission-controller",
               "replicas" : 2,
               "requestsCpu" : "250m",
               "requestsMem" : "512Mi"
             }, {
               "limitsCpu" : "500m",
               "limitsMem" : "512Mi",
               "name" : "node-local-dns-cache",
               "requestsCpu" : "25m",
               "requestsMem" : "5Mi"
             } ],
             "size" : "large"
           }
         }
       }
     },
     "status" : {
       "phase" : "Running",
       "version" : "1.6.36",
       "reason" : "Install complete",
       "resources" : [ {
         "limits" : {
           "cpu" : "500m",
           "memory" : "512Mi"
         },
         "requests" : {
           "cpu" : "25m",
           "memory" : "5Mi"
         },
         "involvedObject" : {
           "kind" : "DaemonSet",
           "namespace" : "kube-system",
           "name" : "node-local-dns",
           "uid" : "755437e4-b591-406c-a512-f9a02794082b",
           "apiVersion" : "apps/v1",
           "resourceVersion" : "702874"
         }
       }, {
         "limits" : {
           "cpu" : "250m",
           "memory" : "512Mi"
         },
         "requests" : {
           "cpu" : "250m",
           "memory" : "512Mi"
         },
         "involvedObject" : {
           "kind" : "Deployment",
           "namespace" : "kube-system",
           "name" : "node-local-dns-admission-controller",
           "uid" : "a770edcf-15c2-4caa-b10e-344de7eea7e1",
           "apiVersion" : "apps/v1",
           "resourceVersion" : "705195"
         },
         "replicas" : 2
       } ]
     }
   }

**Status code: 400**

Bad request

.. code-block::

   {
     "error_code" : "ModelArts.50004000",
     "error_msg" : "Bad request. invalid nodepool name"
   }

Status Codes
------------

=========== ==================
Status Code Description
=========== ==================
200         Request succeeded.
400         Bad request
=========== ==================

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
