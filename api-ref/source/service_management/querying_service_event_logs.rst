Querying Service Event Logs
===========================

Function
--------

This API is used to query service event logs, including service operation records, key actions during deployment, and deployment failure causes.

URI
---

GET /v1/{project_id}/services/{service_id}/events

`Table 1 <#modelarts030155enustopic0192973542table10624434011>`__ describes the required parameters. 

.. _modelarts030155enustopic0192973542table10624434011:

.. table:: **Table 1** Parameters

   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                                                                      |
   +============+===========+========+==================================================================================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see `Obtaining a Project ID and Name <../common_parameters/obtaining_a_project_id_and_name.html#modelarts030147>`__. |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | service_id | Yes       | String | Service ID                                                                                                                                                                       |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+



.. _modelarts030155enustopic0192973542table118011654615:

.. table:: **Table 2** Parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                          |
   +=================+=================+=================+======================================================================================================================+
   | event_type      | No              | String          | Type of the event to be filtered. By default, the event type is not filtered. Options:                               |
   |                 |                 |                 |                                                                                                                      |
   |                 |                 |                 | -  **normal**: normal events                                                                                         |
   |                 |                 |                 | -  **abnormal**: abnormal events                                                                                     |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------+
   | start_time      | No              | Number          | Start time of the event to be filtered. The value is milliseconds between the current time and '1970.1.1 0:0:0 UTC'. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------+
   | end_time        | No              | Number          | End time of the event to be filtered. The value is milliseconds between the current time and '1970.1.1 0:0:0 UTC'.   |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------+
   | offset          | No              | Integer         | Start page of the paging list. Default value: **0**                                                                  |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | Maximum number of records returned on each page. Default value: **1000**                                             |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------+
   | sort_by         | No              | String          | Specified sorting field. The default value is **occur_time**.                                                        |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------+
   | order           | No              | String          | Sorting mode. The default value is **desc**. Options:                                                                |
   |                 |                 |                 |                                                                                                                      |
   |                 |                 |                 | -  **asc**: ascending order                                                                                          |
   |                 |                 |                 | -  **desc**: descending order                                                                                        |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------+

Request Body
------------

None

Response Body
-------------

`Table 3 <#modelarts030155enustopic0192973542table413209485>`__ describes the response parameters. 

.. _modelarts030155enustopic0192973542table413209485:

.. table:: **Table 3** Parameters

   +--------------+-----------------+--------------------------------------------------------------------------------------------------+
   | Parameter    | Type            | Description                                                                                      |
   +==============+=================+==================================================================================================+
   | service_id   | String          | Service ID                                                                                       |
   +--------------+-----------------+--------------------------------------------------------------------------------------------------+
   | service_name | String          | Service name                                                                                     |
   +--------------+-----------------+--------------------------------------------------------------------------------------------------+
   | events       | **event** array | Event logs. For details, see `Table 4 <#modelarts030155enustopic0192973542table974014115493>`__. |
   +--------------+-----------------+--------------------------------------------------------------------------------------------------+
   | total_count  | Integer         | Total number of events that meet the search criteria when no paging is implemented               |
   +--------------+-----------------+--------------------------------------------------------------------------------------------------+
   | count        | Integer         | Number of events in the query result                                                             |
   +--------------+-----------------+--------------------------------------------------------------------------------------------------+



.. _modelarts030155enustopic0192973542table974014115493:

.. table:: **Table 4** **event** structure

   +------------+--------+------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Type   | Description                                                                                                            |
   +============+========+========================================================================================================================+
   | occur_time | Number | Time when an event occurs. The value is milliseconds between the current time and '1970.1.1 0:0:0 UTC'.                |
   +------------+--------+------------------------------------------------------------------------------------------------------------------------+
   | event_type | String | Event type. Possible values are **normal** and **abnormal**, indicating whether the event is normal or abnormal.       |
   +------------+--------+------------------------------------------------------------------------------------------------------------------------+
   | event_info | String | Event information,' including service operation records, key actions during deployment, and deployment failure causes. |
   +------------+--------+------------------------------------------------------------------------------------------------------------------------+

Samples
-------

The following example queries event information of the service whose ID is **35de3ca9-1bca-4ae7-9cb0-914f30fa7d3e**.

-  Sample request

   .. code-block::

      GET    https://endpoint/v1/{project_id}/services/{service_id}/events

-  Sample response

   .. code-block::

      {
      "service_id": "35de3ca9-1bca-4ae7-9cb0-914f30fa7d3e",
      "service_name": "zcjtest-07085",
      "count": 9,
      "total_count": 9,
      "events": [
          {
              "occur_time": 1562597251764,
              "event_type": "normal",
              "event_info": "start to deploy service"
          },
          {
              "occur_time": 1562597251788,
              "event_type": "normal",
              "event_info": "building image for model [zcjtestTF 3.0.0]"
          },
          {
              "occur_time": 1562597251805,
              "event_type": "normal",
              "event_info": "model (zcjtestTF 3.0.0) build image success"
          },
          {
              "occur_time": 1562597255744,
              "event_type": "normal",
              "event_info": "preparing environment"
          },
          {
              "occur_time": 1562597275915,
              "event_type": "normal",
              "event_info": "[zcjtestTF 3.0.0] prepare environment success"
          },
          {
              "occur_time": 1562597275921,
              "event_type": "normal",
              "event_info": "[zcjtestTF 3.0.0] schedule resource success"
          },
          {
              "occur_time": 1562597275928,
              "event_type": "normal",
              "event_info": "[zcjtestTF 3.0.0] pulling model image"
          },
          {
              "occur_time": 1562597332570,
              "event_type": "normal",
              "event_info": "[zcjtestTF 3.0.0] pull image success"
          },
          {
              "occur_time": 1562597332582,
              "event_type": "normal",
              "event_info": "[zcjtestTF 3.0.0] starting model"
          }
      ]
      }

Status Code
-----------

For details about the status code, see `Table 1 <../common_parameters/status_code.html#modelarts030094enustopic0132773864table1450010510213>`__.


