:original_name: modelarts_13_0065.html

.. _modelarts_13_0065:

Alarm Status of a Deployed Real-Time Service
============================================

Symptom
-------

A deployed real-time service is in the **Alarm** state.

Solution
--------

The prediction using a real-time service that is in the **Alarm** state may fail. Perform the following operations to locate the fault and deploy the service again:

#. Check whether there are too many prediction requests on the backend.

   If you call APIs for prediction, check whether there are too many prediction requests. A large number of prediction requests lead to the alarm state of the real-time service.

#. Check whether the service memory is functional.

   Check whether memory overflow or leakage occurs in the inference code.

#. Check whether the model is running properly.

   If the model fails, for example, the associated resources are faulty, check inference logs.
