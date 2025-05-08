:original_name: modelarts_03_0405.html

.. _modelarts_03_0405:

Managing ModelArts Authorization
================================

This section describes how to manage agency authorization by calling ModelArts APIs.

Overview
--------

The process of managing ModelArts authorization is as follows:

#. Obtain a user token, which will be added in a request header for authentication.
#. Call the API for :ref:`creating a ModelArts agency <createmodelartsagency>` to create an agency for ModelArts-dependent services, such as OBS and SWR.
#. Call the API for :ref:`configuring authorization <createauthorization>` to configure ModelArts authorization. The administrator can use this API to set an agency for IAM users and set the access key of the current user.

   .. note::

      ModelArts functions, such as data management, training management, development environment, and real-time services, can be used only after being authorized.

#. Call the API for :ref:`obtaining the authorization list <getauthorizations>` to view the authorization.
#. Call the API for :ref:`deleting authorization <deleteauthorizations>` to delete the authorization of a specified user or all users.

Prerequisites
-------------

-  You have obtained the .
-  The following information is available: region where ModelArts is deployed, :ref:`project name and ID <modelarts_03_0147>`, :ref:`account name and ID <modelarts_03_0148>`, and :ref:`username and ID <modelarts_03_0006>`.

Procedure
---------

#. Call the API for :ref:`creating a ModelArts agency <createmodelartsagency>` to create an agency for ModelArts-dependent services, such as OBS, SWR, and IEF.

   a. Request body:

      URI: POST https://*{endpoint}*/v2/*{project_id}*/agency

      Request header:

      -  X-auth-Token →\ *MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...*
      -  Content-Type →application/json

      Request body:

      .. code-block::

         {
           "agency_name_suffix" : "iam-user01"
         }

      Set the italic parameters based on site requirements.

      -  *endpoint*: ModelArts endpoint
      -  *project_id*: Your project ID
      -  **X-auth-Token**: Token obtained in the previous step
      -  **agency_name_suffix**: Customized suffix of the agency name

   b. Response body with status code **200 OK** returned (indicating that **ma_agency_iam-user01** has been created):

      .. code-block::

         {
             "agency_name": "ma_agency_iam-user01"
         }

#. Call the API for :ref:`configuring authorization <createauthorization>` to configure ModelArts authorization. The administrator can use this API to set an agency for IAM users and set the access key of the current user.

   a. Request body:

      URI: POST https://*{endpoint}*/v2/*{project_id}*/authorizations

      Request header:

      -  X-auth-Token →\ *MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...*
      -  Content-Type →application/json

      Request body:

      .. code-block::

         {
           "user_id": "****af917080f5d21f55c018ba19****",
           "type": "agency",
           "content": "ma_agency_iam-user01"
         }

      Set the italic parameters based on site requirements. Set **user_id** to the IAM user ID and **content** to the ModelArts agency created in the previous step.

   b. Response body with status code **200 OK** returned (indicating that the authorization configuration is complete):

      .. code-block::

         {
             "result": true
         }

#. Call the API for :ref:`obtaining the authorization list <getauthorizations>` to view the authorization.

   a. Request body:

      URI: GET https://*{endpoint}*/v2/*{project_id}*/authorizations

      Request header: X-auth-Token →\ *MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...*

      Set the italic parameters based on site requirements.

   b. Response body with status code **200 OK** returned:

      .. code-block::

         {
           "auth": [
             {
               "create_time": 1622804433221,
               "user_id": "all-users",
               "user_name": "all-users",
               "type": "agency",
               "content": "modelarts_agency"
             },
             {
               "create_time": 1625457065365,
               "user_id": "****af917080f5d21f55c018ba19****",
               "user_name": null,
               "type": "agency",
               "content": "ma_agency_iam-user01"
             }
           ],
           "total_count": 2
         }

      Obtain the authorization information based on the response.

#. Call the API for :ref:`deleting authorization <deleteauthorizations>` to delete the authorization of a specified user or all users.

   a. Request body:

      URI: DELETE https://*{endpoint}*/v2/*{project_id}*/authorizations?user_id=\ ``****d80fb058844ae8b82aa66d9fe****``

      Request header: X-auth-Token →\ *MIIZmgYJKoZIhvcNAQcCoIIZizCCGYcCAQExDTALBglghkgBZQMEAgEwgXXXXXX...*

      Set the italic parameters based on site requirements. Set ``****d80fb058844ae8b82aa66d9fe****`` to the IAM user ID of the specified user.

   b. Response body with status code **200 OK** returned (indicating that the authorization has been deleted):

      .. code-block::

         {
             "result": true
         }

   c. If \**user_id*\* is set to \**all-users**, the authorization of all IAM users will be deleted. Response body with status code **200 OK** returned (indicating that the authorization has been deleted):

      .. code-block::

         {
             "result": true,
             "success_message": "Delete all-users auth info successfully!"
         }
