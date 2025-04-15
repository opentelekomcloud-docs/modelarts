:original_name: modelarts_05_3204.html

.. _modelarts_05_3204:

Error "APIG.XXXX" Occurred in a Prediction Failure
==================================================

A request is intercepted on API Gateway due to a fault, and error "APIG.XXXX" occurs.

Rectify the fault by referring to the methods provided in the following typical cases:

-  :ref:`APIG.0101 Incorrect Prediction URL <en-us_topic_0000002233899332__en-us_topic_0000001388983990_section18200525195012>`
-  :ref:`APIG.0201 Request Body Oversized <en-us_topic_0000002233899332__en-us_topic_0000001388983990_section2467112382015>`
-  :ref:`APIG.0301 Authentication Failed <en-us_topic_0000002233899332__en-us_topic_0000001388983990_section362711496297>`

For more details about API Gateway error codes and solutions, see .

.. _en-us_topic_0000002233899332__en-us_topic_0000001388983990_section18200525195012:

APIG.0101 Incorrect Prediction URL
----------------------------------

If the prediction URL is incorrect, API Gateway intercepts the request and reports error message "APIG.0101:The API does not exist or has not been published in the environment". In this case, go to the real-time service details page and obtain the correct API address on the **Usage Guides** tab page.

.. note::

   If you have specified a custom path in the configuration file, add this path to the called API path. For example, if you have specified custom path **/predictions/poetry**, the called API path will be *{API address}*\ **/predictions/poetry**.


.. figure:: /_static/images/en-us_image_0000002268819445.png
   :alt: **Figure 1** Obtaining an API address

   **Figure 1** Obtaining an API address

.. _en-us_topic_0000002233899332__en-us_topic_0000001388983990_section2467112382015:

APIG.0201 Request Body Oversized
--------------------------------

If a request body is oversized, API Gateway intercepts the request and reports error message "APIG.0201:Request entity too large". Reduce the prediction request body and try again.

If you perform prediction by calling an API address, the maximum size of the request body is 12 MB. If the size of the request body exceeds 12 MB, the request will be intercepted.

If you perform prediction on the **Prediction** tab of the service details page, the maximum size of the request body is 8 MB. The size limit varies between the two tab pages because they use different network links.


.. figure:: /_static/images/en-us_image_0000002233740272.png
   :alt: **Figure 2** Request error APIG.0201

   **Figure 2** Request error APIG.0201

.. _en-us_topic_0000002233899332__en-us_topic_0000001388983990_section362711496297:

APIG.0301 Authentication Failed
-------------------------------

If an API is called for service prediction or a token is used for application authentication, a correct token must be obtained. If the token is invalid, API Gateway intercepts the request and reports error message "APIG.0301:Incorrect IAM authentication information: decrypt token fail". Obtain the correct token and enter it in **X-Auth-Token** for prediction.

To obtain a token in a region, obtain the endpoint for this region and the **resource-path** (**/v3/auth/tokens**) in the URI of the API that is used to obtain a user token. Then, construct the URL as follows:

.. code-block::

   https://{iam-endpoint}/v3/auth/tokens
