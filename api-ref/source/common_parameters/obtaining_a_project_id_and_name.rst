.. _modelarts_03_0147:

Obtaining a Project ID and Name
===============================

Scenarios
---------

A project ID or name is required for some requests when an API is called. Therefore, obtain the project ID and name before calling the API. Use either of the following methods:

-  :ref:`Obtaining a Project ID and Name from the Console <modelarts_03_0147__en-us_topic_0171436477_section1747620762418>`
-  :ref:`Obtaining a Project ID by Calling an API <modelarts_03_0147__en-us_topic_0171436477_section3926171216207>`

.. _modelarts_03_0147__en-us_topic_0171436477_section1747620762418:

Obtaining a Project ID and Name from the Console
------------------------------------------------

To do so, perform the following operations:

#. Log in to the console.
#. In the upper right corner, click your account avatar icon and choose **My Settings** from the drop-down list.
#. On the **My Settings** page, go to the **Project List** tab page, which is displayed by default. View the project ID and name in the project list.

.. _modelarts_03_0147__en-us_topic_0171436477_section3926171216207:

Obtaining a Project ID by Calling an API
----------------------------------------

The API for obtaining a project ID is **GET https://**\ *{iam-endpoint}*\ **/v3/projects**. To obtain *{iam-endpoint}*, see :ref:`Request URI <modelarts_03_0005__en-us_topic_0129435569_en-us_topic_0170917207_en-us_topic_0168405763_section1849899574>`\ :ref:`Endpoints <modelarts_03_0141>`.

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
