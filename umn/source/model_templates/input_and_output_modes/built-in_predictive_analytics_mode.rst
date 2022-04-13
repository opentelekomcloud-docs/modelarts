.. _modelarts_23_0102:

Built-in Predictive Analytics Mode
==================================

Input
-----

This is a built-in input and output mode for predictive analytics. The models using this mode are identified as predictive analytics models. The prediction request path is **/**, the request protocol is **HTTP**, the request method is **POST**, and **Content-Type** is **application/json**. The request body is in JSON format. For details about the JSON fields, see :ref:`Table 1 <modelarts_23_0102__en-us_topic_0172873544_table101531747125712>`. Before selecting this mode, ensure that your model can process the input data in **JSON Schema** format.

.. _modelarts_23_0102__en-us_topic_0172873544_table101531747125712:

.. table:: **Table 1** JSON field description

   +-------+----------------+----------------------------------------------------------------------------------------------------------------+
   | Field | Type           | Description                                                                                                    |
   +=======+================+================================================================================================================+
   | data  | Data structure | Inference data. For details, see :ref:`Table 2 <modelarts_23_0102__en-us_topic_0172873544_table159187574436>`. |
   +-------+----------------+----------------------------------------------------------------------------------------------------------------+

.. _modelarts_23_0102__en-us_topic_0172873544_table159187574436:

.. table:: **Table 2** **Data** description

   ======== ============= ======================
   Field    Type          Description
   ======== ============= ======================
   req_data ReqData array List of inference data
   ======== ============= ======================

**ReqData** is of the **Object** type and indicates the inference data. The data structure is determined by the application scenario. For models using this mode, the preprocessing logic in the custom model inference code should be able to correctly process the data inputted in the format defined by the mode.

The **JSON Schema** of a prediction request is as follows:

.. code-block::

   {
       "type": "object",
       "properties": {
           "data": {
               "type": "object",
               "properties": {
                   "req_data": {
                       "items": [{
                           "type": "object",
                           "properties": {}
                       }],
                       "type": "array"
                   }
               }
           }
       }
   }

Output
------

The inference result is returned in JSON format. For details about the JSON fields, see :ref:`Table 3 <modelarts_23_0102__en-us_topic_0172873544_table49621346461>`.

.. _modelarts_23_0102__en-us_topic_0172873544_table49621346461:

.. table:: **Table 3** JSON field description

   +-------+----------------+----------------------------------------------------------------------------------------------------------------+
   | Field | Type           | Description                                                                                                    |
   +=======+================+================================================================================================================+
   | data  | Data structure | Inference data. For details, see :ref:`Table 4 <modelarts_23_0102__en-us_topic_0172873544_table196311344469>`. |
   +-------+----------------+----------------------------------------------------------------------------------------------------------------+

.. _modelarts_23_0102__en-us_topic_0172873544_table196311344469:

.. table:: **Table 4** **Data** description

   ========= ============== ==========================
   Field     Type           Description
   ========= ============== ==========================
   resp_data RespData array List of prediction results
   ========= ============== ==========================

Similar to **ReqData**, **RespData** is also of the **Object** type and indicates the prediction result. Its structure is determined by the application scenario. For models using this mode, the postprocessing logic in the custom model inference code should be able to correctly output data in the format defined by the mode.

The **JSON Schema** of a prediction result is as follows:

.. code-block::

   {
       "type": "object",
       "properties": {
           "data": {
               "type": "object",
               "properties": {
                   "resp_data": {
                       "type": "array",
                       "items": [{
                           "type": "object",
                           "properties": {}
                       }]
                   }
               }
           }
       }
   }

Sample Request
--------------

In this mode, input the data to be predicted in JSON format. The prediction result is returned in JSON format. The following are examples:

-  Performing prediction on the console

   On the **Prediction** tab page of the service details page, enter inference code and click **Predict** to obtain the prediction result.

-  Using Postman to call a RESTful API for prediction

   After a model is deployed as a service, you can obtain the API URL on the **Usage Guides** tab page of the service details page.

   -  On the **Headers** tab page, set **Content-Type** to **application/json** and **X-Auth-Token** to the actual token obtained.
   -  On the **Body** tab page, edit the data to be predicted and click **send** to send your prediction request.
