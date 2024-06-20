:original_name: modelarts_03_0003.html

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

:ref:`Figure 1 <en-us_topic_0000001910007948__en-us_topic_0170917209_en-us_topic_0168405765_fig4865141011511>` shows the response header fields for the API used to obtain a user token.

**x-subject-token** is the desired user token. This token can then be used to authenticate the calling of other APIs.

.. _en-us_topic_0000001910007948__en-us_topic_0170917209_en-us_topic_0168405765_fig4865141011511:

.. figure:: /_static/images/en-us_image_0000001943967489.png
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
       "error_msg": "The format of message is error",
       "error_code": "AS.0001"
   }

In the error response body, **error_code** is an error code, and **error_msg** provides information about the error. For more details, see :ref:`Error Codes <modelarts_03_0095>`.
