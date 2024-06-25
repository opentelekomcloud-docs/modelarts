:original_name: modelarts_13_0221.html

.. _modelarts_13_0221:

Request Timed Out
=================

Symptom
-------

A service prediction request timed out.

Possible Causes
---------------

If a request times out, there is a high probability that the request is intercepted by API Gateway. Check the API Gateway and model.

Solution
--------

#. Run the **:curl -kv** *{Prediction address}* command on the local host to check whether the API Gateway is reachable. If the request timed out, check the local firewall, proxy, and network configurations.
#. Check whether the model is started or the duration for the model to process a single request. Due to the limitation of API Gateway, the duration of a single prediction cannot exceed 40s. If the duration exceeds 40s, the system will return a timeout error by default.
