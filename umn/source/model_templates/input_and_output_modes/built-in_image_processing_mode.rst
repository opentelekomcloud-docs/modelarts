.. _modelarts_23_0101:

Built-in Image Processing Mode
==============================

Input
-----

The built-in image processing input and output mode can be applied to models such as image classification, object detection, and image semantic segmentation. The prediction request path is **/**, the request protocol is **HTTPS**, the request method is **POST**, **Content-Type** is **multipart/form-data**, **key** is **images**, and **type** is **file**. Before selecting this mode, ensure that your model can process the input data whose **key** is **images**.

Output
------

The inference result is returned in JSON format. The specific fields are determined by the model.

Sample Request
--------------

In this mode, input an image to be processed in the inference request. The response in JSON format varies according to the model. The following are examples:

-  Performing prediction on the console

-  Using Postman to call a RESTful API for prediction

   After a model is deployed as a service, you can obtain the API URL on the **Usage Guides** tab page of the service details page. On the **Body** tab page, set the request body. Set **key** to **images**, select **File**, select the image to be processed, and click **send** to send your prediction request.
