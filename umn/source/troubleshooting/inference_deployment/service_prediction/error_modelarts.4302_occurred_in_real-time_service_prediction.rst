:original_name: modelarts_13_0218.html

.. _modelarts_13_0218:

Error ModelArts.4302 Occurred in Real-Time Service Prediction
=============================================================

Symptom
-------

After a real-time service is deployed and running, an inference request is sent to the service, but error ModelArts.4302 occurred.

Cause Analysis and Solution
---------------------------

Error ModelArts.4302 may occur in multiple scenarios. The following describes two typical scenarios:

#. "error_msg": "Gateway forwarding error. Failed to invoke backend service due to connection refused. "

   This error occurs in either of the following cases:

   -  The traffic exceeded the threshold that can be processed by the model. In this case, reduce the traffic or increase the number of model instances.
   -  The image is faulty. In this case, separately run the image and check whether it is functional.

#. "error_msg": "Due to self protection, the backend service is disconnected, please wait moment."

   This error occurs due to excessive number of model errors. A large number of model errors trigger dispatcher circuit breaker, leading to a prediction failure. In this case, check the result returned by the model and handle these errors. Adjust request parameters or reduce the request traffic for higher model calling success rate.
