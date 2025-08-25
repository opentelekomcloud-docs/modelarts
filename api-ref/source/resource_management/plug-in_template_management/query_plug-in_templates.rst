:original_name: ListPluginTemplates.html

.. _ListPluginTemplates:

Query Plug-in Templates
=======================

Function
--------

This API is used to obtain plug-in templates.

URI
---

GET /v2/{project_id}/plugintemplates

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                              |
   +============+===========+========+==========================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                            |
   +==============+===========+========+========================================================================================================================================+
   | templateName | No        | String | Plug-in name. If this parameter is set, the plug-in with the specified name is queried.                                                |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------+
   | poolName     | No        | String | Resource pool name. If this parameter is set, the list of plug-ins that meet the resource pool's installation requirements is queried. |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +------------+----------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | Parameter  | Type                                                                                               | Description                                                                   |
   +============+====================================================================================================+===============================================================================+
   | kind       | String                                                                                             | API type. The value is fixed at **PluginTemplateList** and cannot be changed. |
   +------------+----------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | apiVersion | String                                                                                             | API version. The value is fixed at **v2** and cannot be changed.              |
   +------------+----------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------+
   | items      | Array of :ref:`PluginTemplateV2 <en-us_topic_0000002374896517__response_plugintemplatev2>` objects | List of plug-in templates.                                                    |
   +------------+----------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------+

.. _en-us_topic_0000002374896517__response_plugintemplatev2:

.. table:: **Table 4** PluginTemplateV2

   +-----------------------+------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                                 | Description                                                                     |
   +=======================+======================================================================================================+=================================================================================+
   | apiVersion            | String                                                                                               | API version. Options:                                                           |
   |                       |                                                                                                      |                                                                                 |
   |                       |                                                                                                      | -  **v2**                                                                       |
   +-----------------------+------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
   | kind                  | String                                                                                               | Resource type. Options:                                                         |
   |                       |                                                                                                      |                                                                                 |
   |                       |                                                                                                      | -  **PluginTemplate**: plug-in template                                         |
   +-----------------------+------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
   | metadata              | :ref:`PluginTemplateMetadata <en-us_topic_0000002374896517__response_plugintemplatemetadata>` object | Plug-in template metadata.                                                      |
   +-----------------------+------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
   | spec                  | :ref:`PluginTemplateSpecV2 <en-us_topic_0000002374896517__response_plugintemplatespecv2>` object     | Detailed information about the plug-in template, for example, the version list. |
   +-----------------------+------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+

.. _en-us_topic_0000002374896517__response_plugintemplatemetadata:

.. table:: **Table 5** PluginTemplateMetadata

   +-------------+--------------------+----------------------------------------------------------------+
   | Parameter   | Type               | Description                                                    |
   +=============+====================+================================================================+
   | name        | String             | Plug-in template name                                          |
   +-------------+--------------------+----------------------------------------------------------------+
   | annotations | Map<String,String> | Plug-in template annotations in the format of key-value pairs. |
   +-------------+--------------------+----------------------------------------------------------------+

.. _en-us_topic_0000002374896517__response_plugintemplatespecv2:

.. table:: **Table 6** PluginTemplateSpecV2

   +-----------------------+------------------------------------------------------------------------------------------------------------------+---------------------------------------------+
   | Parameter             | Type                                                                                                             | Description                                 |
   +=======================+==================================================================================================================+=============================================+
   | optional              | Boolean                                                                                                          | Controls whether the plug-in is mandatory.  |
   +-----------------------+------------------------------------------------------------------------------------------------------------------+---------------------------------------------+
   | type                  | String                                                                                                           | Plug-in template type. Options:             |
   |                       |                                                                                                                  |                                             |
   |                       |                                                                                                                  | -  **helm**: Helm type                      |
   |                       |                                                                                                                  |                                             |
   |                       |                                                                                                                  | -  **ccePlugin**: CCE type                  |
   +-----------------------+------------------------------------------------------------------------------------------------------------------+---------------------------------------------+
   | logoURL               | String                                                                                                           | URL of the logo image.                      |
   +-----------------------+------------------------------------------------------------------------------------------------------------------+---------------------------------------------+
   | description           | String                                                                                                           | Plug-in template description.               |
   +-----------------------+------------------------------------------------------------------------------------------------------------------+---------------------------------------------+
   | versions              | Array of :ref:`PluginTemplateVersionV2 <en-us_topic_0000002374896517__response_plugintemplateversionv2>` objects | Details about the plug-in template version. |
   +-----------------------+------------------------------------------------------------------------------------------------------------------+---------------------------------------------+

.. _en-us_topic_0000002374896517__response_plugintemplateversionv2:

.. table:: **Table 7** PluginTemplateVersionV2

   ================= ====== ========================================
   Parameter         Type   Description
   ================= ====== ========================================
   version           String Version number of the plug-in template.
   creationTimestamp String Creation time.
   inputs            Object Plug-in installation parameters.
   translate         Object Translation information used by the GUI.
   description       String Version description.
   detail            String Version description.
   ================= ====== ========================================

**Status code: 404**

.. table:: **Table 8** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   error_code String Error code
   error_msg  String Error message
   ========== ====== =============

Example Requests
----------------

The following is an example of how to query details about node-local-dns plug-in templates.

.. code-block::

   /v2/${projectId}/plugintemplates?templateName=node-local-dns

   {
     "kind" : "PluginTemplateList",
     "apiVersion" : "v2",
     "items" : [ {
       "kind" : "PluginTemplate",
       "apiVersion" : "v2",
       "metadata" : {
         "name" : "node-local-dns",
         "annotations" : {
           "os.modelarts.plugin/release.name" : "NodeLocal DNSCache"
         }
       },
       "spec" : {
         "optional" : true,
         "versions" : [ {
           "version" : "1.6.63",
           "description" : "NodeLocal DNSCache improves Cluster DNS performance by running a dns caching agent on cluster nodes as a DaemonSet.",
           "creationTimestamp" : "2023-05-20T08:50:31Z",
           "inputs" : {
             "parameters" : {
               "custom" : {
                 "annotations" : { },
                 "enable_dnsconfig_admission" : true,
                 "enable_namespace_admission" : true,
                 "image" : {
                   "args" : {
                     "healthPort" : 8080,
                     "interfaceName" : "nodelocaldns",
                     "setupIptables" : false,
                     "skipTeardown" : true,
                     "skipteardown" : true,
                     "syncInterval" : "1ns",
                     "upstreamSvc" : "coredns"
                   },
                   "name" : "node-cache",
                   "pullPolicy" : "Always"
                 },
                 "multiAZBalance" : false,
                 "multiAZEnabled" : false,
                 "nameserver" : "",
                 "ndots" : "5",
                 "node_match_expressions" : [ ],
                 "search" : "",
                 "tolerations" : [ {
                   "effect" : "NoExecute",
                   "key" : "node.kubernetes.io/not-ready",
                   "operator" : "Exists",
                   "tolerationSeconds" : 60
                 }, {
                   "effect" : "NoExecute",
                   "key" : "node.kubernetes.io/unreachable",
                   "operator" : "Exists",
                   "tolerationSeconds" : 60
                 } ],
                 "zones" : [ {
                   "plugins" : {
                     "cache" : {
                       "denial" : { },
                       "parameters" : 30,
                       "prefetch" : { },
                       "server_stale" : false,
                       "success" : { }
                     },
                     "debug" : false,
                     "errors" : true,
                     "forward" : {
                       "expire" : "",
                       "force_tcp" : false,
                       "health_check" : "",
                       "max_fails" : "",
                       "parameters" : "__PILLAR__UPSTREAM__SERVERS__",
                       "policy" : "",
                       "prefer_udp" : false
                     },
                     "log" : {
                       "classes" : "all",
                       "format" : "combined"
                     },
                     "prometheus" : true,
                     "reload" : true
                   },
                   "zone" : ".:53"
                 }, {
                   "plugins" : {
                     "cache" : {
                       "parameters" : 30
                     },
                     "debug" : false,
                     "errors" : true,
                     "forward" : {
                       "force_tcp" : true,
                       "parameters" : "__PILLAR__CLUSTER__DNS__"
                     },
                     "log" : {
                       "classes" : "all",
                       "format" : "combined"
                     },
                     "prometheus" : true,
                     "reload" : true
                   },
                   "zone" : "ip6.arpa:53"
                 }, {
                   "plugins" : {
                     "cache" : {
                       "parameters" : 30
                     },
                     "debug" : false,
                     "errors" : true,
                     "forward" : {
                       "force_tcp" : true,
                       "parameters" : "__PILLAR__CLUSTER__DNS__"
                     },
                     "log" : {
                       "classes" : "all",
                       "format" : "combined"
                     },
                     "prometheus" : true,
                     "reload" : true
                   },
                   "zone" : "in-addr.arpa:53"
                 }, {
                   "plugins" : {
                     "cache" : {
                       "denial" : {
                         "size" : 9984,
                         "ttl" : 5
                       },
                       "parameters" : 30,
                       "prefetch" : { },
                       "success" : {
                         "size" : 9984,
                         "ttl" : 30
                       }
                     },
                     "debug" : false,
                     "errors" : true,
                     "forward" : {
                       "force_tcp" : true,
                       "parameters" : "__PILLAR__CLUSTER__DNS__"
                     },
                     "health" : {
                       "port" : 8080
                     },
                     "log" : {
                       "classes" : "all",
                       "format" : "combined"
                     },
                     "prometheus" : true,
                     "reload" : true
                   },
                   "zone" : "cluster.local:53"
                 } ]
               },
               "flavor1" : {
                 "description" : "High avaiable",
                 "is_default" : true,
                 "name" : "HA",
                 "replicas" : 2,
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
               },
               "flavor2" : {
                 "description" : "Has only one instance",
                 "name" : "Single",
                 "replicas" : 1,
                 "resources" : [ {
                   "limitsCpu" : "250m",
                   "limitsMem" : "512Mi",
                   "name" : "node-local-dns-admission-controller",
                   "replicas" : 1,
                   "requestsCpu" : "250m",
                   "requestsMem" : "512Mi"
                 }, {
                   "limitsCpu" : "500m",
                   "limitsMem" : "512Mi",
                   "name" : "node-local-dns-cache",
                   "requestsCpu" : "25m",
                   "requestsMem" : "5Mi"
                 } ],
                 "size" : "small"
               },
               "flavor3" : {
                 "description" : "custom resources",
                 "name" : "custom-resources",
                 "replicas" : 2,
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
                 "size" : "custom"
               }
             }
           },
           "translate" : {
             "zh_CN" : {
               "description" : {
                 "Parameters" : {
                   "flavor1" : {
                     "description" : "Dual pods for the automatic DNSConfig injection controller increase the reliability of the plug-in.",
                     "name" : "High availability"
                   },
                   "flavor2" : {
                     "description" : "Single-instance deployment",
                     "name" : "Single-instance"
                   },
                   "flavor3" : {
                     "description" : "Custom resource specifications for deployment",
                     "name" : "Custom"
                   }
                 },
                 "Parameters.flavor1.description" : "Dual pods for the automatic DNSConfig injection controller increase the reliability of the plug-in.",
                 "Parameters.flavor1.name" : "High availability",
                 "Parameters.flavor2.description" : "Single-instance deployment",
                 "Parameters.flavor2.name" : "Single-instance",
                 "Parameters.flavor3.description" : "Custom resource specifications for deployment",
                 "Parameters.flavor3.name" : "Custom"
               },
               "key" : null,
               "plugintemplate" : {
                 "changeLog" : "Kubernetes v1.31 is supported. The admission-controller logs have been updated to stdout logs. node-local-dns supports custom health check ports.",
                 "components" : {
                   "node-local-dns-admission-controller" : {
                     "description" : "Automatically adds DNSConfig to pods. The node-local-dNS-cache address is injected into the container's **/etc/resolv.conf** file. The container service then uses the local cache for DNS domain name resolution.",
                     "kind" : "Deployment"
                   },
                   "node-local-dns-cache" : {
                     "description" : "Deploys a DNS cache proxy on each cluster node to boost DNS performance.",
                     "kind" : "DaemonSet"
                   }
                 },
                 "description" : "NodeLocal DNSCache is a set of daemons running on cluster nodes. NodeLocal DNSCache improves cluster DNS performance by using DNS cache proxies."
               }
             }
           }
         } ],
         "logoURL" : "https://obs.com/plugintemplates/node-local-dnslogo.svg"
       }
     } ]
   }

Example Responses
-----------------

**Status code: 200**

Request succeeded.

.. code-block::

   {
     "kind" : "PluginTemplateList",
     "apiVersion" : "v2",
     "items" : [ {
       "kind" : "PluginTemplate",
       "apiVersion" : "v2",
       "metadata" : {
         "name" : "node-local-dns",
         "annotations" : {
           "os.modelarts.plugin/release.name" : "NodeLocal DNSCache"
         }
       },
       "spec" : {
         "optional" : true,
         "versions" : [ {
           "version" : "1.6.63",
           "description" : "NodeLocal DNSCache improves Cluster DNS performance by running a dns caching agent on cluster nodes as a DaemonSet.",
           "creationTimestamp" : "2023-05-20T08:50:31Z",
           "inputs" : {
             "parameters" : {
               "custom" : {
                 "annotations" : { },
                 "enable_dnsconfig_admission" : true,
                 "enable_namespace_admission" : true,
                 "image" : {
                   "args" : {
                     "healthPort" : 8080,
                     "interfaceName" : "nodelocaldns",
                     "setupIptables" : false,
                     "skipTeardown" : true,
                     "skipteardown" : true,
                     "syncInterval" : "1ns",
                     "upstreamSvc" : "coredns"
                   },
                   "name" : "node-cache",
                   "pullPolicy" : "Always"
                 },
                 "multiAZBalance" : false,
                 "multiAZEnabled" : false,
                 "nameserver" : "",
                 "ndots" : "5",
                 "node_match_expressions" : [ ],
                 "search" : "",
                 "tolerations" : [ {
                   "effect" : "NoExecute",
                   "key" : "node.kubernetes.io/not-ready",
                   "operator" : "Exists",
                   "tolerationSeconds" : 60
                 }, {
                   "effect" : "NoExecute",
                   "key" : "node.kubernetes.io/unreachable",
                   "operator" : "Exists",
                   "tolerationSeconds" : 60
                 } ],
                 "zones" : [ {
                   "plugins" : {
                     "cache" : {
                       "denial" : { },
                       "parameters" : 30,
                       "prefetch" : { },
                       "server_stale" : false,
                       "success" : { }
                     },
                     "debug" : false,
                     "errors" : true,
                     "forward" : {
                       "expire" : "",
                       "force_tcp" : false,
                       "health_check" : "",
                       "max_fails" : "",
                       "parameters" : "__PILLAR__UPSTREAM__SERVERS__",
                       "policy" : "",
                       "prefer_udp" : false
                     },
                     "log" : {
                       "classes" : "all",
                       "format" : "combined"
                     },
                     "prometheus" : true,
                     "reload" : true
                   },
                   "zone" : ".:53"
                 }, {
                   "plugins" : {
                     "cache" : {
                       "parameters" : 30
                     },
                     "debug" : false,
                     "errors" : true,
                     "forward" : {
                       "force_tcp" : true,
                       "parameters" : "__PILLAR__CLUSTER__DNS__"
                     },
                     "log" : {
                       "classes" : "all",
                       "format" : "combined"
                     },
                     "prometheus" : true,
                     "reload" : true
                   },
                   "zone" : "ip6.arpa:53"
                 }, {
                   "plugins" : {
                     "cache" : {
                       "parameters" : 30
                     },
                     "debug" : false,
                     "errors" : true,
                     "forward" : {
                       "force_tcp" : true,
                       "parameters" : "__PILLAR__CLUSTER__DNS__"
                     },
                     "log" : {
                       "classes" : "all",
                       "format" : "combined"
                     },
                     "prometheus" : true,
                     "reload" : true
                   },
                   "zone" : "in-addr.arpa:53"
                 }, {
                   "plugins" : {
                     "cache" : {
                       "denial" : {
                         "size" : 9984,
                         "ttl" : 5
                       },
                       "parameters" : 30,
                       "prefetch" : { },
                       "success" : {
                         "size" : 9984,
                         "ttl" : 30
                       }
                     },
                     "debug" : false,
                     "errors" : true,
                     "forward" : {
                       "force_tcp" : true,
                       "parameters" : "__PILLAR__CLUSTER__DNS__"
                     },
                     "health" : {
                       "port" : 8080
                     },
                     "log" : {
                       "classes" : "all",
                       "format" : "combined"
                     },
                     "prometheus" : true,
                     "reload" : true
                   },
                   "zone" : "cluster.local:53"
                 } ]
               },
               "flavor1" : {
                 "description" : "High avaiable",
                 "is_default" : true,
                 "name" : "HA",
                 "replicas" : 2,
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
               },
               "flavor2" : {
                 "description" : "Has only one instance",
                 "name" : "Single",
                 "replicas" : 1,
                 "resources" : [ {
                   "limitsCpu" : "250m",
                   "limitsMem" : "512Mi",
                   "name" : "node-local-dns-admission-controller",
                   "replicas" : 1,
                   "requestsCpu" : "250m",
                   "requestsMem" : "512Mi"
                 }, {
                   "limitsCpu" : "500m",
                   "limitsMem" : "512Mi",
                   "name" : "node-local-dns-cache",
                   "requestsCpu" : "25m",
                   "requestsMem" : "5Mi"
                 } ],
                 "size" : "small"
               },
               "flavor3" : {
                 "description" : "custom resources",
                 "name" : "custom-resources",
                 "replicas" : 2,
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
                 "size" : "custom"
               }
             }
           },
           "translate" : {
             "zh_CN" : {
               "description" : {
                 "Parameters" : {
                   "flavor1" : {
                     "description" : "Dual pods for the automatic DNSConfig injection controller increase the reliability of the plug-in.",
                     "name" : "High availability"
                   },
                   "flavor2" : {
                     "description" : "Single-instance deployment",
                     "name" : "Single-instance"
                   },
                   "flavor3" : {
                     "description" : "Custom resource specifications for deployment",
                     "name" : "Custom"
                   }
                 },
                 "Parameters.flavor1.description" : "Dual pods for the automatic DNSConfig injection controller increase the reliability of the plug-in.",
                 "Parameters.flavor1.name" : "High availability",
                 "Parameters.flavor2.description" : "Single-instance deployment",
                 "Parameters.flavor2.name" : "Single-instance",
                 "Parameters.flavor3.description" : "Custom resource specifications for deployment",
                 "Parameters.flavor3.name" : "Custom"
               },
               "key" : null,
               "plugintemplate" : {
                 "changeLog" : "Kubernetes v1.31 is supported. The admission-controller logs have been updated to stdout logs. node-local-dns supports custom health check ports.",
                 "components" : {
                   "node-local-dns-admission-controller" : {
                     "description" : "Automatically adds DNSConfig to pods. The node-local-dNS-cache address is injected into the container's **/etc/resolv.conf** file. The container service then uses the local cache for DNS domain name resolution.",
                     "kind" : "Deployment"
                   },
                   "node-local-dns-cache" : {
                     "description" : "Deploys a DNS cache proxy on each cluster node to boost DNS performance.",
                     "kind" : "DaemonSet"
                   }
                 },
                 "description" : "NodeLocal DNSCache is a set of daemons running on cluster nodes. NodeLocal DNSCache improves cluster DNS performance by using DNS cache proxies."
               }
             }
           }
         } ],
         "logoURL" : "https://obs.com/plugintemplates/node-local-dnslogo.svg"
       }
     } ]
   }

**Status code: 404**

Not found.

.. code-block::

   {
     "error_code" : "ModelArts.50005101",
     "error_msg" : "Plugintemplate {name} not found."
   }

Status Codes
------------

=========== ==================
Status Code Description
=========== ==================
200         Request succeeded.
404         Not found.
=========== ==================

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
