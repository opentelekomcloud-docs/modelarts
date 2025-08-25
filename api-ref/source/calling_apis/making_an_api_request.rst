:original_name: modelarts_03_0005.html

.. _modelarts_03_0005:

Making an API Request
=====================

This section describes the structure of a REST API request, and uses the IAM API for obtaining a user token as an example to demonstrate how to call an API. The obtained token can then be used to authenticate the calling of other APIs.

.. _en-us_topic_0000002374896665__en-us_topic_0170917207_en-us_topic_0168405763_section1849899574:

Request URI
-----------

The format of a request URI is as follows:

**{URI-scheme} :// {Endpoint} / {resource-path} ? {query-string}**

.. table:: **Table 1** Request URI

   +---------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter     | Description                                                                                                                                                                                                                                                  |
   +===============+==============================================================================================================================================================================================================================================================+
   | URI-scheme    | Protocol used to transmit requests. All APIs use HTTPS.                                                                                                                                                                                                      |
   +---------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Endpoint      | Domain name or IP address of the server for the REST service endpoint. The endpoint varies depending on services in different regions. It can be obtained in :ref:`Endpoint <en-us_topic_0000002374896637__section2081352311426>`.                           |
   +---------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | resource-path | Access path of an API for performing a specified operation. Obtain the value from the URI of an API. For example, the **resource-path** of the API used to obtain a user token is **/v3/auth/tokens**.                                                       |
   +---------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | query-string  | Query parameter, which is optional. Ensure that a question mark (?) is included before a query parameter that is in the format of "Parameter name=Parameter value". For example, **limit=10** indicates that a maximum of 10 data records will be displayed. |
   +---------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

For example, to obtain an IAM token in a region, obtain the endpoint of IAM for this region and the **resource-path** (**/v3/auth/tokens**) in the URI of the API used to obtain a user token.

.. code-block::

   https://{iam-endpoint}/v3/auth/tokens

.. note::

   To simplify the URI display, each API is provided with only a **resource-path** and a request method. The **URI-scheme** of all APIs is HTTPS, and the endpoints of all APIs in the same region are identical.

Request Methods
---------------

HTTP defines the following request methods that can be used to send a request to the server.

.. table:: **Table 2** HTTP methods

   +-----------------------------------+------------------------------------------------------------------------------------------------------+
   | Method                            | Description                                                                                          |
   +===================================+======================================================================================================+
   | GET                               | Request the server to return specified resources.                                                    |
   +-----------------------------------+------------------------------------------------------------------------------------------------------+
   | PUT                               | Request the server to update specified resources.                                                    |
   +-----------------------------------+------------------------------------------------------------------------------------------------------+
   | POST                              | Request the server to add resources or perform special operations.                                   |
   +-----------------------------------+------------------------------------------------------------------------------------------------------+
   | DELETE                            | Request the server to delete specified resources, for example, an object.                            |
   +-----------------------------------+------------------------------------------------------------------------------------------------------+
   | HEAD                              | Request header.                                                                                      |
   +-----------------------------------+------------------------------------------------------------------------------------------------------+
   | PATCH                             | Request the server to update partial content of a specified resource.                                |
   |                                   |                                                                                                      |
   |                                   | If the requested resource does not exist, the server may create the resource using the PATCH method. |
   +-----------------------------------+------------------------------------------------------------------------------------------------------+

For example, for the API used to obtain a user token, the request method is POST. The request is as follows:

.. code-block:: text

   POST https://{iam-endpoint}/v3/auth/tokens

Request Header
--------------

You can add additional header fields to a request, such as the fields required by a specified URI or HTTP method. For example, to request for the authentication information, add **Content-Type**, which specifies the request body type.

:ref:`Table 3 <en-us_topic_0000002374896665__table139019272562>` describes common request header fields.

.. _en-us_topic_0000002374896665__table139019272562:

.. table:: **Table 3** Common request headers

   +-----------------+------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Description                                                                                                                        | Mandatory                                                                             | Example                                                                                                                                                                                           |
   +=================+====================================================================================================================================+=======================================================================================+===================================================================================================================================================================================================+
   | Content-type    | Request body type or format. The default value is **application/json**.                                                            | Yes                                                                                   | application/json                                                                                                                                                                                  |
   +-----------------+------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Content-Length  | Length of the request body, in bytes.                                                                                              | Mandatory for POST and PUT requests but must be left blank for GET requests           | 3495                                                                                                                                                                                              |
   +-----------------+------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Project-Id    | Project ID. This parameter is used to obtain a token for each project.                                                             | No                                                                                    | e9993fc787d94b6c886cbaa340f9c0f4                                                                                                                                                                  |
   +-----------------+------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Auth-Token    | User token. It is a response to the API for obtaining a user token. This API is the only one that does not require authentication. | Mandatory for token-based authentication                                              | N/A                                                                                                                                                                                               |
   +-----------------+------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Sdk-Date      | Time when the request is sent. The time is in *YYYYMMDD'T'HHMMSS'Z'* format.                                                       | Mandatory for AK/SK-based authentication, optional for PKI token-based authentication | 20190307T101459Z                                                                                                                                                                                  |
   |                 |                                                                                                                                    |                                                                                       |                                                                                                                                                                                                   |
   |                 | The value is the current GMT time of the system.                                                                                   |                                                                                       |                                                                                                                                                                                                   |
   +-----------------+------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Authorization   | Authentication information.                                                                                                        | Mandatory for AK/SK-based authentication                                              | SDK-HMAC-SHA256 Credential=ZIRRKMTWPTQFQI1WKNKB/20150907//ec2/sdk_request, SignedHeaders=content-type;host;x-sdk-date, Signature=55741b610f3c9fa3ae40b5a8021ebf7ebc2a28a603fc62d25cb3bfe6608e1994 |
   |                 |                                                                                                                                    |                                                                                       |                                                                                                                                                                                                   |
   |                 | The value is obtained from the request signature result and is required when the AK/SK are used to encrypt the signature.          |                                                                                       |                                                                                                                                                                                                   |
   |                 |                                                                                                                                    |                                                                                       |                                                                                                                                                                                                   |
   |                 | Type: string                                                                                                                       |                                                                                       |                                                                                                                                                                                                   |
   |                 |                                                                                                                                    |                                                                                       |                                                                                                                                                                                                   |
   |                 | Default value: none                                                                                                                |                                                                                       |                                                                                                                                                                                                   |
   +-----------------+------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Host            | Server information of the resource being requested. The value can be obtained from the URL of the service API.                     | Mandatory for AK/SK-based authentication                                              | code.test.com                                                                                                                                                                                     |
   |                 |                                                                                                                                    |                                                                                       |                                                                                                                                                                                                   |
   |                 | This value is *host name*\ [:*port number*].                                                                                       |                                                                                       | or                                                                                                                                                                                                |
   |                 |                                                                                                                                    |                                                                                       |                                                                                                                                                                                                   |
   |                 | If the port number is not specified, the default port is used. The default port number for **https** is **443**.                   |                                                                                       | code.test.com:443                                                                                                                                                                                 |
   +-----------------+------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. note::

   In addition to supporting token-based authentication, APIs support authentication using AK/SK. During AK/SK authentication, an SDK is used to sign a request, and the **Authorization** (signature authentication) and **X-Sdk-Date** (time when a request is sent) headers are automatically added to the request.

The API for obtaining a user token does not require authentication. This API only requires adding **Content-Type**. The request with the added **Content-Type** header is as follows:

.. code-block:: text

   POST https://{iam-endpoint}/v3/auth/tokens
   Content-Type: application/json

Request Body
------------

The body of a request is often sent in a structured format as specified in the Content-Type header field. The request body transfers content except the request header.

The request body varies depending on APIs. Some APIs do not require the request body, such as the APIs requested using the GET or DELETE method.

If an API is used to obtain a user token, the request parameters and parameter description can be obtained from the API request. The following provides an example request with a body included. Replace *user_name*, *domain_name*, and *user_password* with the actual username, tenant name, and login password, respectively. **project_name** is the project name. For details, see :ref:`Obtaining a Username <modelarts_03_0006>`, :ref:`Obtaining a Tenant Name and ID <modelarts_03_0148>`, and :ref:`Obtaining a Project Name <modelarts_03_0147>`.

.. note::

   The **scope** parameter specifies where a token takes effect. In the example, the token takes effect only for the resources in a specified project. ModelArts uses a region-specific endpoint to call this API. Set **scope** to **project**. You can set **scope** to an account or a project under an account.

.. code-block:: text

   POST https://{iam-endpoint}/v3/auth/tokens
   Content-Type:application/json
   {
     "auth": {
       "identity": {
         "methods": ["password"],
         "password": {
           "user": {
             "name": "user_name",
             "password": "user_password",
             "domain": {
               "name": "domain_name"
             }
           }
         }
       },
       "scope": {
         "project": {
           "name": "project_name"
         }
       }
     }
   }

After all data required for the API request is available, send the request to call the API through `curl <https://curl.haxx.se/>`__, `Postman <https://www.getpostman.com/>`__, or coding. In the response to the API used to obtain a user token, **x-subject-token** is the desired user token. This token can then be used to authenticate the calling of other APIs.
