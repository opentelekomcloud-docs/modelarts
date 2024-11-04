:original_name: modelarts_13_0216.html

.. _modelarts_13_0216:

Service Prediction Failed
=========================

Symptom
-------

After a real-time service is deployed and running, an inference request is sent to the service, but the inference failed.

Cause Analysis and Solution
---------------------------

Service prediction involves multiple phases, including the client, Internet, APIG, dispatcher, and model service. A fault in any phase may lead to a prediction failure.


.. figure:: /_static/images/en-us_image_0000002079104361.png
   :alt: **Figure 1** Prediction process

   **Figure 1** Prediction process

#. If an "APIG.XXXX" error occurs, the request is intercepted on API Gateway due to a fault.

   Rectify the fault by referring to :ref:`Error "APIG.XXXX" Occurred in a Prediction Failure <modelarts_05_3204>`.

   The following shows the other cases in which a request is intercepted on API Gateway:

   -  :ref:`Method Not Allowed <modelarts_13_0220>`
   -  :ref:`Request Timed Out <modelarts_13_0221>`

#. If a "ModelArts.XXXXX" error occurs, the request is intercepted on the dispatcher due to a fault.

   Rectify the fault by referring to the methods provided in the following typical cases:

   -  :ref:`Error ModelArts.4302 Occurred in Real-Time Service Prediction <modelarts_13_0218>`
   -  :ref:`Error ModelArts.4302 Occurred in Real-Time Service Prediction <modelarts_13_0218>`
   -  :ref:`Error ModelArts.4503 Occurred in Real-Time Service Prediction <modelarts_13_0219>`

#. If an inference image is used and an "MR.XXXX" error occurs, the request has been sent to the model service, and the fault is generally due to a bug in model inference code.

   Identify the cause of the prediction failure based on the error information in logs, debug the model inference code, and import the model again for prediction.

   Rectify the fault by referring to :ref:`Error MR.0105 Occurred in Real-Time Service Prediction <modelarts_13_0192>`.

#. In other cases, check whether the client and the Internet are accessible.

#. If the fault persists, contact the system administrator.
