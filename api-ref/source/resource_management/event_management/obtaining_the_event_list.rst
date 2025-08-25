:original_name: ListEvents.html

.. _ListEvents:

Obtaining the Event List
========================

Function
--------

This API is used to obtain the event list.

URI
---

GET /v1/{project_id}/events

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                              |
   +============+===========+========+==========================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                      |
   +=================+=================+=================+==================================================================================================================================================================================+
   | resource        | Yes             | String          | Type of the resource for which an event occurs. Options:                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                  |
   |                 |                 |                 | -  **pools**: resource pool                                                                                                                                                      |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name            | Yes             | String          | ID of the resource for which an event occurs.                                                                                                                                    |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | Maximum number of records on each page. If this parameter is left blank or set to **0**, 500 records are returned by default. A maximum of 500 records are allowed on each page. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset          | No              | Integer         | Offset of the pagination query. This parameter is left blank when the first page is queried.                                                                                     |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type            | No              | String          | Event type. Options:                                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                                  |
   |                 |                 |                 | -  **Normal**: queries normal events.                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                  |
   |                 |                 |                 | -  **Warning**: queries alarm events.                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                  |
   |                 |                 |                 |    If this parameter is left blank, all types of events are returned.                                                                                                            |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | since           | No              | Integer         | Event start timestamp                                                                                                                                                            |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | until           | No              | Integer         | Event end timestamp                                                                                                                                                              |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ascend          | No              | Boolean         | Whether the results are sorted in ascending order                                                                                                                                |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------------------+------------------------------------------------------------------------------+------------------------------+
   | Parameter             | Type                                                                         | Description                  |
   +=======================+==============================================================================+==============================+
   | apiVersion            | String                                                                       | API version. Options:        |
   |                       |                                                                              |                              |
   |                       |                                                                              | -  **v1**                    |
   +-----------------------+------------------------------------------------------------------------------+------------------------------+
   | kind                  | String                                                                       | Resource type. Options:      |
   |                       |                                                                              |                              |
   |                       |                                                                              | -  **EventList**: event list |
   +-----------------------+------------------------------------------------------------------------------+------------------------------+
   | items                 | Array of :ref:`Event <en-us_topic_0000002374896485__response_event>` objects | Events                       |
   +-----------------------+------------------------------------------------------------------------------+------------------------------+
   | total                 | Integer                                                                      | Total number of events       |
   +-----------------------+------------------------------------------------------------------------------+------------------------------+

.. _en-us_topic_0000002374896485__response_event:

.. table:: **Table 4** Event

   +-----------------------+-----------------------+------------------------------------------------+
   | Parameter             | Type                  | Description                                    |
   +=======================+=======================+================================================+
   | apiVersion            | String                | API version. Options:                          |
   |                       |                       |                                                |
   |                       |                       | -  **v1**                                      |
   +-----------------------+-----------------------+------------------------------------------------+
   | kind                  | String                | Resource type. Options:                        |
   |                       |                       |                                                |
   |                       |                       | -  **Event**: event                            |
   +-----------------------+-----------------------+------------------------------------------------+
   | type                  | String                | Event type. Options:                           |
   |                       |                       |                                                |
   |                       |                       | -  **Normal**: normal event                    |
   |                       |                       |                                                |
   |                       |                       | -  **Warning**: abnormal event                 |
   +-----------------------+-----------------------+------------------------------------------------+
   | firstTimestamp        | String                | Time when an event occurred for the first time |
   +-----------------------+-----------------------+------------------------------------------------+
   | lastTimestamp         | String                | Time when an event occurred for the last time  |
   +-----------------------+-----------------------+------------------------------------------------+
   | count                 | Integer               | Consecutive occurrences of an event            |
   +-----------------------+-----------------------+------------------------------------------------+
   | reason                | String                | Event cause                                    |
   +-----------------------+-----------------------+------------------------------------------------+
   | message               | String                | Event details                                  |
   +-----------------------+-----------------------+------------------------------------------------+

**Status code: 400**

.. table:: **Table 5** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   error_code String Error code
   error_msg  String Error message
   ========== ====== =============

**Status code: 404**

.. table:: **Table 6** Response body parameters

   ========== ====== =============
   Parameter  Type   Description
   ========== ====== =============
   error_code String Error code
   error_msg  String Error message
   ========== ====== =============

Example Requests
----------------

Querying events of resource pool **pool-6f5da086876d4cd084d36f8bd3346036** by page

.. code-block:: text

   GET https://{endpoint}/v1/{project_id}/events?resource=pools&name=pool-5ff6-6f5da086876d4cd084d36f8bd3346036&limit=10&offset=0&ascend=false

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "kind" : "EventList",
     "apiVersion" : "v1",
     "metadata" : {
       "continue" : "52eddc13-cfad-42d3-aee4-92fea5813e7f"
     },
     "items" : [ {
       "kind" : "Event",
       "apiVersion" : "v1",
       "type" : "Warning",
       "firstTimestamp" : "2022-12-30T02:16:19Z",
       "lastTimestamp" : "2022-12-30T02:16:19Z",
       "count" : 1,
       "reason" : "PoolResourcesStatusChange",
       "message" : "Pool resources status changed, available/abnormal/creating/deleting count from 1/0/0/0 to 0/1/0/0, timestamp: 1672366579."
     }, {
       "kind" : "Event",
       "apiVersion" : "v1",
       "type" : "Normal",
       "firstTimestamp" : "2023-01-02T09:02:45Z",
       "lastTimestamp" : "2023-01-02T09:02:45Z",
       "count" : 1,
       "reason" : "PoolResourcesStatusChange",
       "message" : "Pool resources status changed, available/abnormal/creating/deleting count from 0/1/0/0 to 1/0/0/0, timestamp: 1672650165."
     }, {
       "kind" : "Event",
       "apiVersion" : "v1",
       "type" : "Warning",
       "firstTimestamp" : "2023-01-16T06:55:35Z",
       "lastTimestamp" : "2023-01-16T06:55:35Z",
       "count" : 1,
       "reason" : "PoolStatusChange",
       "message" : "Pool status changed, from Running to Abnormal, details: ."
     }, {
       "kind" : "Event",
       "apiVersion" : "v1",
       "type" : "Warning",
       "firstTimestamp" : "2023-01-16T06:57:51Z",
       "lastTimestamp" : "2023-01-16T06:57:51Z",
       "count" : 1,
       "reason" : "PoolResourcesStatusChange",
       "message" : "Pool resources status changed, available/abnormal/creating/deleting count from 1/0/0/0 to 0/1/0/0, timestamp: 1673852271."
     }, {
       "kind" : "Event",
       "apiVersion" : "v1",
       "type" : "Normal",
       "firstTimestamp" : "2023-01-29T02:29:04Z",
       "lastTimestamp" : "2023-01-29T02:29:04Z",
       "count" : 1,
       "reason" : "PoolStatusChange",
       "message" : "Pool status changed, from Abnormal to Running."
     } ]
   }

**Status code: 400**

Bad request

.. code-block::

   {
     "error_code" : "ModelArts.50004000",
     "error_msg" : "Bad request."
   }

**Status code: 404**

Not found

.. code-block::

   {
     "error_code" : "ModelArts.50015001",
     "error_msg" : "Pool {name} not found."
   }

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
200         OK
400         Bad request
404         Not found
=========== ===========

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
