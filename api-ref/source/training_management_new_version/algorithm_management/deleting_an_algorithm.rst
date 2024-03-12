:original_name: DeleteAlgorithm.html

.. _DeleteAlgorithm:

Deleting an Algorithm
=====================

Function
--------

This API is used to delete an algorithm.

URI
---

DELETE /v2/{project_id}/algorithms/{algorithm_id}

.. table:: **Table 1** Path Parameters

   +--------------+-----------+--------+---------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                     |
   +==============+===========+========+=================================================================================+
   | project_id   | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID <modelarts_03_0147>`. |
   +--------------+-----------+--------+---------------------------------------------------------------------------------+
   | algorithm_id | Yes       | String | Algorithm ID.                                                                   |
   +--------------+-----------+--------+---------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

None

Example Requests
----------------

The following shows how to modify the algorithm whose UUID is **2e5451fe-913f-4492-821a-2981031382f7**.

.. code-block:: text

   DELETE     https://endpoint/v2/{project_id}/algorithms/2e5451fe-913f-4492-821a-2981031382f7

Example Responses
-----------------

**Status code: 202**

No Content

.. code-block::

   null

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
202         No Content
=========== ===========

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
