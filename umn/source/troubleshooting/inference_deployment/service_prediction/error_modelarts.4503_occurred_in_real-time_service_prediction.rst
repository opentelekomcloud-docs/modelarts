:original_name: modelarts_13_0219.html

.. _modelarts_13_0219:

Error ModelArts.4503 Occurred in Real-Time Service Prediction
=============================================================

Symptom
-------

After a real-time service is deployed and running, an inference request is sent to the service, but error ModelArts.4503 occurred.

Cause Analysis and Solution
---------------------------

Error ModelArts.4503 may occur in multiple scenarios. The following describes typical scenarios:

#. Communication error

   Request error: {"error_code":"ModelArts.4503","error_msg":"Failed to respond due to backend service not found or failed to respond"}

   To ensure high performance, ModelArts reuses the connections to the same model service. According to the TCP protocol, a disconnection can be initiated either by the client or server of a connection. Disconnecting a connection requires a four-way handshake. If the model service (server) initiates a disconnection, but the connection is being used by ModelArts (client), a communication error occurs and this error code is returned.

   If your model is imported from a custom image, set **keep-alive** of the web server used by the custom image to a larger value. This prevents a disconnection request initiated from the server. If you use Gunicorn as the web server, configure the **keep-alive** value by running the **Gunicorn** command. Models imported from other sources have been configured in the service.

#. Protocol error

   Request error: {"error_code":"ModelArts.4503", "error_msg":"Failed to find backend service because SSL error in the backend service, please check the service is https"}

   If the model used for deploying a real-time service is imported from a container image, this error occurs when the protocol used by the container API is incorrectly configured.

   For security purposes, all ModelArts inference requests are HTTPS-compliant. When you import a model from a container image, ModelArts allows the image to use HTTPS or HTTP. However, you must specify the protocol used by the image in **Container API**.

   If the **Container API** value is inconsistent with the value provided by your image, for example, **Container API** is set to **HTTPS** but your image actually uses HTTP, the preceding error occurs.

   To resolve this issue, create an AI application version, select the correct protocol (HTTP or HTTPS), and deploy a real-time service again or update the existing real-time service.

#. Long prediction time

   The following error is reported: {"error_code": "ModelArts.4503", "error_msg": "Failed to find backend service because response timed out, please confirm your service is able to process the request without timeout. "}

   Due to the limitation of API Gateway, the prediction duration of each request does not exceed 40 seconds. A prediction is successful if the entire process takes a time not longer than the time limit. The process involves sending data to ModelArts, performing prediction, and sending the prediction result back. If a prediction takes a time longer than the time limit or ModelArts cannot respond to frequent prediction requests, this error occurs.

   Take the following measures to resolve this issue:

   -  If a prediction request is oversized, the request times out due to slow data processing. In this case, optimize the prediction code to shorten the prediction time.
   -  A complex model leads to slow inference. Optimize the model to shorten the prediction time.
   -  Increase the number of instances or select a compute node flavor with better performance. For example, use GPUs instead of CPUs to improve the service processing performance.

#. Service error

   The following error is reported: {"error_code": "ModelArts.4503","error_msg": "Backend service respond timeout, please confirm your service is able to process the request without timeout. "}

   Service logs are as follows:

   .. code-block::

      [2022-10-24 11:37:31 +0000] [897] [INFO] Booting worker with pid: 897
      [2022-10-24 11:41:47 +0000] [1997] [INFO] Booting worker with pid: 1997
      [2022-10-24 11:41:22 +0000] [1897] [INFO] Booting worker with pid: 1897
      [2022-10-24 11:37:54 +0000] [997] [INFO] Booting worker with pid: 997

   The service malfunctions and restarts repeatedly. As a result, prediction requests cannot be sent to the service instance.

   Take the following measures to resolve this issue:

   -  Reduce the number of prediction requests and check whether the fault is resolved. If the fault does not recur, the service process exits due to heavy load. In this case, increase the number of instances or improve the instance specifications.
   -  The inference code is defective. Debug the code to rectify the fault.
