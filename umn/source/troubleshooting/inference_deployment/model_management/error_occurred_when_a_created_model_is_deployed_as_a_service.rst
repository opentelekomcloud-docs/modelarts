:original_name: modelarts_13_0212.html

.. _modelarts_13_0212:

Error Occurred When a Created Model Is Deployed as a Service
============================================================

Symptom
-------

After a model is created, an error occurred when it is deployed as a service.

Possible Causes
---------------

When a model is imported using a custom or base image, many service logics are customized. Any error in the logics will result in a service deployment or prediction failure.

Solution
--------

#. After deploying a service failed, go to the service details page and view deployment logs to identify the failure cause. (Ensure that standard input and output functions are used for code output. Otherwise, the output will not be displayed on the ModelArts console.) Find the code based on the error in the logs to locate the fault.
