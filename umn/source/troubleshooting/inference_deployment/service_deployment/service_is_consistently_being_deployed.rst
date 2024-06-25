:original_name: modelarts_05_3187.html

.. _modelarts_05_3187:

Service Is Consistently Being Deployed
======================================

Symptom
-------

A service retains in the **Deploying** state. No obvious error is found in AI application logs.

Possible Causes
---------------

The AI application port is typically incorrect. Check whether the port for creating the AI application is correct.

Solution
--------

Check the AI application port. If it is not configured, the default port 8080 is used. If you have changed the port number in the configuration file of the custom image, configure the correct port number when deploying the AI application.

For details, see :ref:`How Do I Change the Default Port to Create a Real-Time Service Using a Custom Image? <modelarts_06_0004>`
