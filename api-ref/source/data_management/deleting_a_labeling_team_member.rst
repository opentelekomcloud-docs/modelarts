:original_name: DeleteWorker.html

.. _DeleteWorker:

Deleting a Labeling Team Member
===============================

Function
--------

This API is used to delete a labeling team member.

Debugging
---------

You can debug this API through automatic authentication in or use the SDK sample code generated by API Explorer.

URI
---

DELETE /v2/{project_id}/workforces/{workforce_id}/workers/{worker_id}

.. table:: **Table 1** Path Parameters

   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                               |
   +==============+===========+========+===========================================================================================================================+
   | project_id   | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+
   | worker_id    | Yes       | String | ID of a labeling team member.                                                                                             |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+
   | workforce_id | Yes       | String | ID of a labeling team.                                                                                                    |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

None

Example Requests
----------------

Deleting a Labeling Team Member

.. code-block:: text

   DELETE https://{endpoint}/v2/{project_id}/workforces/{workforce_id}/workers/{worker_id}

Example Responses
-----------------

**Status code: 204**

No Content

.. code-block::

   { }

Status Codes
------------

=========== ============
Status Code Description
=========== ============
204         No Content
401         Unauthorized
403         Forbidden
=========== ============

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
