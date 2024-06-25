:original_name: modelarts_21_0019.html

.. _modelarts_21_0019:

Deploying a Model as a Service
==============================

Deploying a Model
-----------------

You can deploy a model as a real-time service that provides a real-time test UI and monitoring capabilities. After the model is trained, you can deploy a **Successful** version with ideal accuracy as a service. The procedure is as follows:

#. On the **Train Model** tab page, wait until the training status changes to **Completed**. Click **Deploy** in the **Version Manager** pane.

#. In the displayed **Deploy** dialog box, set **Specifications**, and click **OK** to deploy the model as a real-time service.

   -  **Specifications**: The GPU specifications are better, and the CPU specifications are more cost-effective.

   -  **Compute Nodes**: The default value is **1** and cannot be changed.

   -  **Auto Stop**: After this function is enabled and the auto stop time is set, a service automatically stops at the specified time. If this function is disabled, a real-time service will continue to run. The auto stop function is enabled by default. The default value is **1 hour later**.

      The options are **1 hour later**, **2 hours later**, **4 hours later**, **6 hours later**, and **Custom**. If you select **Custom**, enter any integer from 1 to 24 in the text box on the right.

#. After the model deployment is started, view the deployment status on the **Service Deployment** page.

   It takes a certain period of time to deploy a model. When the status in the **Version Manager** pane changes from **Deploying** to **Running**, the deployment is complete.

Testing the Service
-------------------

-  On the **Service Deployment** page, select a service type. For example, on the ExeML page, the object detection model is deployed as a real-time service by default. On the **Real-Time Services** page, click **Prediction** in the **Operation** column of the target service to perform a service test.
-  The following describes the procedure for performing a service test after the predictive analytics model is deployed as a service on the ExeML page.

   #. After the model is deployed, you can test the model using code. On the **ExeML** page, click the target project, go to the **Deploy Service** tab page, select a service version in the **Running** state, and enter the code in the **Service Test** pane.
   #. Click **Predict** to perform the test. After the prediction is complete, the result is displayed in the **Test Result** pane on the right. If the model accuracy does not meet your expectation, train and deploy the model again on the **Label Data** tab page. If you are satisfied with the model prediction result, call the API to access the real-time service as prompted. For details, see "Accessing a Real-Time Service".

      -  **attr_1** to **attr_4** indicate the input data. On the **Label Data** tab page, the selected label column is **attr_5**, indicating that **attr_5** is the target column to be predicted.

         ::

            {
                "data": {
                    "req_data": [{
                        "attr_1": 5.1,
                        "attr_2": 3.5,
                        "attr_3": 1.4,
                        "attr_4": 0.2
                    }]
                }
            }

      -  In the preceding code snippet, **predict** is the inference result of label column **attr_5**.

      .. note::

         A running real-time service keeps consuming resources. If you do not need to use the real-time service, click **Stop** in the **Version Manager** pane to stop the service. If you want to use the service again, click **Start**.
