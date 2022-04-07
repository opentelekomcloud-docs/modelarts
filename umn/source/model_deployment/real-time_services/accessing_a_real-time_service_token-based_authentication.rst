.. _modelarts_23_0063:

Accessing a Real-Time Service (Token-based Authentication)
==========================================================

If a real-time service is in the **Running** state, the real-time service has been deployed successfully. This service provides a standard RESTful API for users to call. Before integrating the API to the production environment, commission the API. You can use either of the following methods to send an inference request to the real-time service:

:ref:`Method 1: Use GUI-based Software for Inference (Postman) <modelarts_23_0063__en-us_topic_0165025308_section959354162911>` (Postman is recommended for Windows.)

:ref:`Method 2: Run the cURL Command to Send an Inference Request <modelarts_23_0063__en-us_topic_0165025308_section104131434203114>` (curl commands are recommended for Linux.)

.. _modelarts_23_0063__en-us_topic_0165025308_section959354162911:

Method 1: Use GUI-based Software for Inference (Postman)
--------------------------------------------------------

#. Download Postman and install it, or install the Postman Chrome extension. Alternatively, use other software that can send POST requests. Postman 7.24.0 is recommended.
#. Open Postman.
#. Set parameters on Postman. The following uses image classification as an example.

   -  Select a POST task and copy the API URL to the POST text box. To obtain the API URL of the real-time service, switch to the **Usage Guides** tab on the page providing details about the real-time service. On the **Headers** tab page, set **Key** to **X-Auth-Token** and **Value** to the obtained token.
   -  On the **Body** tab page, file input and text input are available.

      -  **File input**

         Select **form-data**. Set **KEY** to the input parameter of the model, for example, **images**. Set **VALUE** to an image to be inferred (only one image can be inferred).

      -  **Text input**

         Select **raw** and then **JSON(application/json)**. Enter the request body in the text box below. An example request body is as follows:

         .. code-block::

            {
              "meta": {
                "uuid": "10eb0091-887f-4839-9929-cbc884f1e20e"
              },
              "data": {
                "req_data": [
                  {
                    "sepal_length": 3,
                    "sepal_width": 1,
                    "petal_length": 2.2,
                    "petal_width": 4
                  }
                ]
              }
            }

         **meta** can carry a universally unique identifier (UUID). When you call an API, the system provides a UUID. When the inference result is returned, the UUID is returned to trace the request. If you do not need this function, leave **meta** blank. **data** contains a **req_data** array for one or multiple pieces of input data. The parameters of each piece of data are determined by the model, such as **sepal_length** and **sepal_width** in this example.

#. After setting the parameters, click **Send** to send the request. The result is displayed in the response.

   -  Inference result using file input: The field values in the return result vary with the model.
   -  Inference result using text input: The request body contains **meta** and **data**. If the request contains **uuid**, **uuid** will be returned in the response. Otherwise, **uuid** is left blank. **data** contains a **resp_data** array for the inference results of one or multiple pieces of input data. The parameters of each result are determined by the model, for example, **sepal_length** and **predictresult** in this example.

.. _modelarts_23_0063__en-us_topic_0165025308_section104131434203114:

Method 2: Run the cURL Command to Send an Inference Request
-----------------------------------------------------------

The command for sending inference requests can be input as a file or text.

#. File input

   .. code-block::

      curl -k -F 'images=@Image path' -H 'X-Auth-Token:Token value' -X POST Real-time service URL

   -  **-k** indicates that SSL websites can be accessed without using a security certificate.
   -  **-F** indicates file input. In this example, the parameter name is **images**, which can be changed as required. The image storage path follows **@**.
   -  **-H** indicates the header of the POST command. **X-Auth-Token** is the **KEY** value on the **Headers** page. *Token value* indicates the obtained token. For details about how to obtain the token, see .
   -  **POST** is followed by the API URL of the real-time service.

   The following is an example of the cURL command for inference with file input:

   .. code-block::

      curl -k -F 'images=@/home/data/test.png' -H 'X-Auth-Token:MIISkAY***80T9wHQ==' -X POST https://modelarts-infers-1.xxx/v1/infers/eb3e0c54-3dfa-4750-af0c-95c45e5d3e83

#. Text input

   .. code-block::

      curl -k -d '{"data":{"req_data":[{"sepal_length":3,"sepal_width":1,"petal_length":2.2,"petal_width":4}]}}' -H 'X-Auth-Token:MIISkAY***80T9wHQ==' -H 'Content-type: application/json' -X POST https://modelarts-infers-1.xxx/v1/infers/eb3e0c54-3dfa-4750-af0c-95c45e5d3e83

   **-d** indicates the text input of the request body.
