:original_name: ShowServiceEvents.html

.. _ShowServiceEvents:

Obtaining Service Event Logs
============================

Function
--------

This API is used to obtain service event logs, including service operation records, key actions during deployment, and deployment failure causes.

URI
---

GET /v1/{project_id}/services/{service_id}/events

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                              |
   +============+===========+========+==========================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | service_id | Yes       | String | Service ID                                                                               |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                           |
   +=================+=================+=================+=======================================================================================+
   | event_type      | No              | String          | Event type. Options:                                                                  |
   |                 |                 |                 |                                                                                       |
   |                 |                 |                 | -  **normal**: normal events                                                          |
   |                 |                 |                 |                                                                                       |
   |                 |                 |                 | -  **abnormal**: abnormal events                                                      |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------+
   | start_time      | No              | Number          | Start time for filtering events. By default, events are not filtered.                 |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------+
   | end_time        | No              | Number          | End time for filtering events. By default, events are not filtered.                   |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------+
   | offset          | No              | Integer         | Start page for pagination display. The default value is **0**.                        |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | Maximum number of records returned on each page. Default value: **1000**              |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------+
   | sort_by         | No              | String          | Specifies the sorting field. The default value is occur_time (event generation time). |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------+
   | order           | No              | String          | Sorting mode. Options:                                                                |
   |                 |                 |                 |                                                                                       |
   |                 |                 |                 | -  **asc**: ascending order                                                           |
   |                 |                 |                 |                                                                                       |
   |                 |                 |                 | -  **des**\ c: descending order, which is the default value                           |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                           |
   +==============+===========+========+=======================================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. It can be obtained by calling the IAM API that is used to obtain a user token. The value of **X-Subject-Token** in the response header is the user token. |
   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +--------------+--------------------------------------------------------------------------------+----------------------------------------------------------------------------------+
   | Parameter    | Type                                                                           | Description                                                                      |
   +==============+================================================================================+==================================================================================+
   | service_name | String                                                                         | Service name                                                                     |
   +--------------+--------------------------------------------------------------------------------+----------------------------------------------------------------------------------+
   | total_count  | Integer                                                                        | Total number of events that meet the search criteria when no paging is performed |
   +--------------+--------------------------------------------------------------------------------+----------------------------------------------------------------------------------+
   | service_id   | String                                                                         | Service ID                                                                       |
   +--------------+--------------------------------------------------------------------------------+----------------------------------------------------------------------------------+
   | count        | Integer                                                                        | Number of events in the query result                                             |
   +--------------+--------------------------------------------------------------------------------+----------------------------------------------------------------------------------+
   | events       | Array of :ref:`Events <en-us_topic_0000002042806692__response_events>` objects | Event logs of a service                                                          |
   +--------------+--------------------------------------------------------------------------------+----------------------------------------------------------------------------------+

.. _en-us_topic_0000002042806692__response_events:

.. table:: **Table 5** Events

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                                                              |
   +=======================+=======================+==========================================================================================================================================================================================================================================================+
   | event_type            | String                | Event type. Options:                                                                                                                                                                                                                                     |
   |                       |                       |                                                                                                                                                                                                                                                          |
   |                       |                       | -  **normal**: normal events                                                                                                                                                                                                                             |
   |                       |                       |                                                                                                                                                                                                                                                          |
   |                       |                       | -  **abnormal**: abnormal events                                                                                                                                                                                                                         |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | event_info            | String                | Event information, which mainly describes the the five phases of the deployment process. More information can be supplemented later. The five phases are image building, environment preparation, resource scheduling, image pulling, and model startup. |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | occur_time            | Number                | Time when an event occurs, in milliseconds calculated from 1970.1.1 0:0:0 UTC.                                                                                                                                                                           |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

.. code-block:: text

   GET https://{endpoint}/v1/{project_id}/services/{service_id}/events

Example Responses
-----------------

**Status code: 200**

Event logs of a service

.. code-block::

   {
     "service_name" : "service-07085",
     "total_count" : 9,
     "service_id" : "35de3ca9-1bca-4ae7-9cb0-914f30fa7d3e",
     "count" : 9,
     "events" : [ {
       "event_type" : "normal",
       "event_info" : "start to deploy service",
       "occur_time" : 1562597251764
     }, {
       "event_type" : "normal",
       "event_info" : "building image for model [TF 3.0.0]",
       "occur_time" : 1562597251788
     }, {
       "event_type" : "normal",
       "event_info" : "model (TF 3.0.0) build image success",
       "occur_time" : 1562597251805
     }, {
       "event_type" : "normal",
       "event_info" : "preparing environment",
       "occur_time" : 1562597255744
     }, {
       "event_type" : "normal",
       "event_info" : "[TF 3.0.0] prepare environment success",
       "occur_time" : 1562597275915
     }, {
       "event_type" : "normal",
       "event_info" : "[TF 3.0.0] schedule resource success",
       "occur_time" : 1562597275921
     }, {
       "event_type" : "normal",
       "event_info" : "[TF 3.0.0] pulling model image",
       "occur_time" : 1562597275928
     }, {
       "event_type" : "normal",
       "event_info" : "[TF 3.0.0] pull image success",
       "occur_time" : 1562597332570
     }, {
       "event_type" : "normal",
       "event_info" : "[TF 3.0.0] starting model",
       "occur_time" : 1562597332582
     } ]
   }

Status Codes
------------

=========== =======================
Status Code Description
=========== =======================
200         Event logs of a service
=========== =======================

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
