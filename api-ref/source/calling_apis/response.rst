.. _modelarts_03_0003:

Response
========

After sending a request, you will receive a response, including the status code, response header, and response body.

Status Code
-----------

A status code is a group of digits, ranging from 1\ *xx* to 5\ *xx*. It indicates the status of a request. For more information, see :ref:`Status Code <modelarts_03_0094>`.

For example, if status code **201** is returned for calling the API used to obtain a user token, the request is successful.

Response Header
---------------

Similar to a request, a response also has a header, for example, **Content-type**.

.. table:: **Table 1** Common response header fields

   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Header                | Description                                                                                                                                                                                                                    | Mandatory             |
   +=======================+================================================================================================================================================================================================================================+=======================+
   | Content-Type          | Media type of the message body sent to a receiver                                                                                                                                                                              | Yes                   |
   |                       |                                                                                                                                                                                                                                |                       |
   |                       | Type: string                                                                                                                                                                                                                   |                       |
   |                       |                                                                                                                                                                                                                                |                       |
   |                       | Default value: **application/json; charset=UTF-8**                                                                                                                                                                             |                       |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | X-request-id          | This field carries the request ID for task tracing.                                                                                                                                                                            | No                    |
   |                       |                                                                                                                                                                                                                                |                       |
   |                       | Type: string **request_id-timestamp-hostname** (**request_id** is the UUID generated on the server, **timestamp** indicates the current timestamp, and **hostname** is the name of the server that processes the current API.) |                       |
   |                       |                                                                                                                                                                                                                                |                       |
   |                       | Default value: none                                                                                                                                                                                                            |                       |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | X-ratelimit           | This field carries the total number of flow control requests.                                                                                                                                                                  | No                    |
   |                       |                                                                                                                                                                                                                                |                       |
   |                       | Type: integer                                                                                                                                                                                                                  |                       |
   |                       |                                                                                                                                                                                                                                |                       |
   |                       | Default value: none                                                                                                                                                                                                            |                       |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | X-ratelimit-used      | This field carries the number of remaining requests.                                                                                                                                                                           | No                    |
   |                       |                                                                                                                                                                                                                                |                       |
   |                       | Type: integer                                                                                                                                                                                                                  |                       |
   |                       |                                                                                                                                                                                                                                |                       |
   |                       | Default value: none                                                                                                                                                                                                            |                       |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | X-ratelimit-window    | This field carries the flow control unit.                                                                                                                                                                                      | No                    |
   |                       |                                                                                                                                                                                                                                |                       |
   |                       | Type: string The unit is minute, hour, or day.                                                                                                                                                                                 |                       |
   |                       |                                                                                                                                                                                                                                |                       |
   |                       | Default value: hour                                                                                                                                                                                                            |                       |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

:ref:`Figure 1 <modelarts_03_0003__en-us_topic_0171310283_en-us_topic_0170917209_en-us_topic_0168405765_fig4865141011511>` shows the response header fields for the API used to obtain a user token.

**x-subject-token** is the desired user token. This token can then be used to authenticate the calling of other APIs.

.. _modelarts_03_0003__en-us_topic_0171310283_en-us_topic_0170917209_en-us_topic_0168405765_fig4865141011511:

.. figure:: /_static/images/en-us_image_0171113090.png
   :alt: **Figure 1** Header fields of the response to the request for obtaining a user token


   **Figure 1** Header fields of the response to the request for obtaining a user token

Response Body
-------------

The body of a response is often returned in structured format as specified in the **Content-Type** header field. The response body transfers content except the response header.

The following is part of the response body for the API used to obtain a user token.

.. code-block::

   {
       "token": {
           "expires_at": "2019-02-13T06:52:13.855000Z",
           "methods": [
               "password"
           ],
           "catalog": [
               {
                   "endpoints": [
                       {
                           "region_id": "aaa",
   ......

If an error occurs during API calling, an error code and a message will be displayed. The following shows an error response body.

.. code-block::

   {
       "error_message": "The format of message is error",
       "error_code": "AS.0001"
   }

In the error response body, **error_code** is an error code, and **error_message** provides information about the error. For more details, see :ref:`Error Codes <modelarts_03_0095>`.
