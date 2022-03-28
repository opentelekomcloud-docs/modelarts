Obtaining a Project ID and Name
===============================

Scenarios
---------

A project ID or name is required for some requests when an API is called. Therefore, obtain the project ID and name before calling the API. Use either of the following methods:

-  `Obtaining a Project ID and Name from the Console <#obtaining-a-project-id-and-name-from-the-console>`__
-  `Obtaining a Project ID by Calling an API <#obtaining-a-project-id-by-calling-an-api>`__

Obtaining a Project ID and Name from the Console
------------------------------------------------

To do so, perform the following operations:

#. Log in to the console.
#. In the upper right corner, click your account avatar icon and choose **My Settings** from the drop-down list.
#. On the **My Settings** page, go to the **Project List** tab page, which is displayed by default. View the project ID and name in the project list.

Obtaining a Project ID by Calling an API
----------------------------------------

The API for obtaining a project ID is **GET https://**\ *{iam-endpoint}*\ **/v3/projects**. To obtain *{iam-endpoint}*, see `Request URI <../calling_apis/making_an_api_request.html#request-uri>`__\ `Endpoints <../before_you_start/endpoints.html>`__.

The following is an example response. For example, if ModelArts is deployed in the **xxx** region, the value of **name** in the response body is **xxx**. The value of **id** in **projects** is the project ID.

.. code-block::

   {
       "projects": [{
           "domain_id": "65382450e8f64ac0870cd180d14e684b",
           "is_domain": false,
           "parent_id": "65382450e8f64ac0870cd180d14e684b",
           "name": "xxx",
           "description": "",
           "links": {
               "next": null,
               "previous": null,
               "self": "https://www.example.com/v3/projects/a4a5d4098fb4474fa22cd05f897d6b99"
           },
           "id": "a4a5d4098fb4474fa22cd05f897d6b99",
           "enabled": true
       }],
       "links": {
           "next": null,
           "previous": null,
           "self": "https://www.example.com/v3/projects"
       }
   }


