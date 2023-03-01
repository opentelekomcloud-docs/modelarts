:original_name: modelarts_23_0070.html

.. _modelarts_23_0070:

Accessing an Edge Service
=========================


Accessing an Edge Service
-------------------------

If the edge service and edge node are in the **Running** status, the edge service has been successfully deployed on the edge node.

You can use either of the following methods to send an inference request to the edge service deployed on the edge node in a network that can access the edge node:

-  :ref:`Method 1: Use GUI-based Software for Inference (Postman) <modelarts_23_0070__en-us_topic_0171858295_section148871319185615>`
-  :ref:`Method 2: Run the cURL Command to Send an Inference Request <modelarts_23_0070__en-us_topic_0171858295_section3383753105619>`

.. _modelarts_23_0070__en-us_topic_0171858295_section148871319185615:

Method 1: Use GUI-based Software for Inference (Postman)
--------------------------------------------------------

#. Download `Postman <https://www.getpostman.com/apps>`__ and install it, or directly add the Postman extension to Google Chrome. (Alternatively, use other software that can send POST requests).
#. Open Postman.
#. Set parameters on Postman. The following uses image classification as an example.

   -  Select a POST task, and copy the URL of the edge node to the POST edit box. View the URL of the edge node on the **Node Info** tab page of the edge service details page.
   -  On the **Body** tab page, input parameters are divided into file input and text input types.

      -  **File input**

         Select **form-data**. Set **KEY** to the input parameter of the model, for example, **images**. Set **VALUE** to an image to be inferred (only one image can be inferred).

      -  **Text input**

         Select **raw** and then select **JSON(application/json)**. Enter the request body in the text box below. An example request body is as follows:

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

         **meta** can carry **uuid**. When the inference result is returned, the UUID is returned to trace the request. If you do not need this function, leave **meta** blank. **data** contains the **req_data** array. You can pass one or more pieces of request data. The parameters of each piece of data are determined by the model, such as **sepal_length** and **sepal_width** in this example.

#. After setting the parameters, click **Send** to send the request. The result is displayed in the response.

   -  In the inference result using file input, the field values may vary with the model.
   -  The request body of inference using text input contains **meta** and **data**. If the request contains **uuid**, **uuid** will be returned in the response. Otherwise, **uuid** is left blank. **data** contains the **req_data** array. You can pass one or more pieces of request data. The parameters of each piece of data are determined by the model, such as **sepal_length** and **sepal_width** in this example.

.. _modelarts_23_0070__en-us_topic_0171858295_section3383753105619:

Method 2: Run the cURL Command to Send an Inference Request
-----------------------------------------------------------

The format for sending inference request commands varies with file input and text input.

#. File input

   .. code-block::

      curl -F 'images=@Image path'-X POST Service address of the edge node

   -  **-F** indicates file input. In this example, the parameter name is **images**, which can be changed as required. The image storage path follows **@**.
   -  **POST** is followed by the URL of the edge node.

   The following is an example of the cURL command for inference with file input:

   .. code-block::

      curl -F 'images=@/home/data/cat.jpg' -X POST http://192.168.0.158:1032

#. Text input

   .. code-block::

      curl -d '{
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
      } '-X POST <Service address of the edge node>

   -  **-d** indicates the text input of the request body. If the model uses text input, this parameter is mandatory.

   The following is an example of the cURL command for inference with text input:

   .. code-block::

      curl -d '{
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
      }' -X POST http://192.168.0.158:1033
