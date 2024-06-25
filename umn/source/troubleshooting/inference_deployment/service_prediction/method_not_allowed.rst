:original_name: modelarts_13_0220.html

.. _modelarts_13_0220:

Method Not Allowed
==================

Symptom
-------

Error message "Method Not Allowed" is displayed during service prediction.

Possible Causes
---------------

The APIs registered by default for service prediction must be called using POST. If you use GET, API Gateway will intercept the request.

Solution
--------

Use POST to call the API.
