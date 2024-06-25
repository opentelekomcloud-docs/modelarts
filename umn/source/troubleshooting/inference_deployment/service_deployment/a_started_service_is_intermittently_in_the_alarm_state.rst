:original_name: modelarts_05_3188.html

.. _modelarts_05_3188:

A Started Service Is Intermittently in the Alarm State
======================================================

Symptom
-------

The traffic for prediction is not heavy, but the following error frequently occurs:

-  Backend service internal error. Backend service read timed out
-  Send the request from gateway to the service failed due to connection refused, please confirm your service is connectable

-  Send the request from gateway to the service failed due to connection timeout, please confirm your service is able to process the new request

Possible Causes
---------------

After a prediction request is sent, the service stops and then starts.

Solution
--------

Check the image used by the service, identify the cause of the service stop, and rectify the fault. Re-create the AI application and use it to deploy a service.
