:original_name: modelarts_13_0062.html

.. _modelarts_13_0062:

Error Occurred When a Custom Image Model Is Deployed as a Real-Time Service
===========================================================================

Symptom
-------

A model fails to be deployed as a real-time service. On the real-time service details page, the message "failed to pull image, retry later" is displayed on the **Events** tab page while no information is displayed on the **Logs** tab page.

Solution
--------

This fault is typically caused by the excessive size of the model you have deployed. Do the following:

-  Simplify the model, re-import it, and deploy it as a real-time service.
-  Purchase a dedicated resource pool and use it to deploy the model as a real-time service.
