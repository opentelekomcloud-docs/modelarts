:original_name: modelarts_05_3207.html

.. _modelarts_05_3207:

Why Did My Service Deployment Fail with Proper Deployment Timeout Configured?
=============================================================================

A model can properly start after a service is deployed. The startup status of a model can be detected through a health check.

Check whether a service is deployed using a health check API for custom images. When creating an AI application, configure a health check delay to ensure the initialization of containers.

It is a good practice to configure a proper health check delay for service deployment.
