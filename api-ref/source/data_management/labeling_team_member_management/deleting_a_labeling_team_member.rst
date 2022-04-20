.. _DeleteWorker:

Deleting a Labeling Team Member
===============================

Function
--------

This API is used to delete a labeling team member.

URI
---

DELETE /v2/{project_id}/workforces/{workforce_id}/workers/{worker_id}

.. table:: **Table 1** Path parameters

   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                        |
   +==============+===========+========+====================================================================================================================+
   | project_id   | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <modelarts_03_0147>`. |
   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | worker_id    | Yes       | String | ID of a labeling team member.                                                                                      |
   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | workforce_id | Yes       | String | ID of a labeling team.                                                                                             |
   +--------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

None

Example Requests
----------------

Deleting a Labeling Team Member

.. code-block::

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
