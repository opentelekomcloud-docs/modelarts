:original_name: modelarts_13_0217.html

.. _modelarts_13_0217:

Error ModelArts.4206 Occurred in Real-Time Service Prediction
=============================================================

Symptom
-------

After a real-time service is deployed and running, an inference request is sent to the service, but error ModelArts.4206 occurred.

Possible Causes
---------------

ModelArts.4206 indicates that the request traffic on an API exceeded the preset threshold. To ensure stable service running, ModelArts limits the inference request traffic on a single API.

Solution
--------

Reduce the inference request traffic on an API. If ultra-high concurrency is required, submit a service ticket.
