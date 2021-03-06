:original_name: AcceptSamples.html

.. _AcceptSamples:

Submitting Sample Review Comments of an Acceptance Task
=======================================================

Function
--------

This API is used to submit sample review comments of an acceptance task.

URI
---

POST /v2/{project_id}/datasets/{dataset_id}/workforce-tasks/{workforce_task_id}/acceptance/batch-comment

.. table:: **Table 1** Path Parameters

   +-------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory | Type   | Description                                                                                                        |
   +===================+===========+========+====================================================================================================================+
   | dataset_id        | Yes       | String | Dataset ID.                                                                                                        |
   +-------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | project_id        | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <modelarts_03_0147>`. |
   +-------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | workforce_task_id | Yes       | String | ID of a labeling task.                                                                                             |
   +-------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request body parameters

   +-----------+-----------+------------------------------------------------------------------------------+----------------------+
   | Parameter | Mandatory | Type                                                                         | Description          |
   +===========+===========+==============================================================================+======================+
   | comments  | No        | Array of :ref:`SampleComment <acceptsamples__request_samplecomment>` objects | Review comment list. |
   +-----------+-----------+------------------------------------------------------------------------------+----------------------+

.. _acceptsamples__request_samplecomment:

.. table:: **Table 3** SampleComment

   +-----------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                                                                                                     |
   +===========+===========+=========+=================================================================================================================================+
   | accept    | Yes       | Boolean | Whether the submitted sample review comments are passed. The options are as follows: - **true**: passed - **false**: not passed |
   +-----------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------+
   | comment   | No        | String  | Review comment, which contains 0 to 256 characters, excluding special characters (!<>=&"').                                     |
   +-----------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------+
   | sample_id | No        | String  | Sample ID.                                                                                                                      |
   +-----------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------+
   | score     | No        | String  | Review score, whose value can be **A**, **B**, **C**, or **D**, in descending order.                                            |
   +-----------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------+
   | worker_id | No        | String  | ID of a labeling team member.                                                                                                   |
   +-----------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Requests
----------------

Submitting Sample Review Comments of an Acceptance Task

.. code-block::

   {
     "comments" : [ {
       "worker_id" : "8c15ad080d3eabad14037b4eb00d6a6f",
       "sample_id" : "09ac49d5b06385849c8769fdcf0f6d60",
       "accept" : true,
       "comment" : "",
       "score" : "A"
     } ]
   }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   { }

Status Codes
------------

=========== ============
Status Code Description
=========== ============
200         OK
401         Unauthorized
403         Forbidden
404         Not Found
=========== ============

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
