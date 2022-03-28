Creating a ModelArts Agency
===========================

Function
--------

This API is used to create an agency so that ModelArts can access dependent services such as OBS, SWR, and IEF.

URI
---

POST /v2/{project_id}/agency

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                                           |
   +============+===========+========+=======================================================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain a project ID, see `Obtaining a Project ID <../common_parameters/obtaining_a_project_id_and_name.html>`__. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------



.. _CreateModelArtsAgencyrequestCreateModelArtsAgencyRequest:

.. table:: **Table 2** Request body parameters

   +--------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+
   | Parameter          | Mandatory       | Type            | Description                                                                                                                |
   +====================+=================+=================+============================================================================================================================+
   | agency_name_suffix | No              | String          | Agency name suffix.                                                                                                        |
   |                    |                 |                 |                                                                                                                            |
   |                    |                 |                 | The parameter contains a maximum of 50 characters.                                                                         |
   |                    |                 |                 |                                                                                                                            |
   |                    |                 |                 | The agency name prefix is consistently to be **ma_agency**.                                                                |
   |                    |                 |                 |                                                                                                                            |
   |                    |                 |                 | For example, if the value of this parameter is **iam-user01**, the name of the created agency is **ma_agency_iam-user01**. |
   |                    |                 |                 |                                                                                                                            |
   |                    |                 |                 | The value of this parameter is left blank by default, indicating that an agency named **modelarts_agency** is created.     |
   +--------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Requests
----------------

Create a ModelArts agency.

.. code-block::

   POST https://{endpoint}/v2/{project_id}/agency

   {
     "agency_name_suffix" : "iam-user01"
   }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "agency_name" : "ma_agency_iam-user01"
   }

Status Codes
------------



.. _CreateModelArtsAgencystatuscode:

=========== ============
Status Code Description
=========== ============
200         OK
400         Bad Request
401         Unauthorized
403         Forbidden
404         Not Found
=========== ============

Error Codes
-----------

See `Error Codes <../common_parameters/error_codes.html>`__.


