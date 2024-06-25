:original_name: modelarts_13_0053.html

.. _modelarts_13_0053:

Failed to Submit the Real-time Service Deployment Task
======================================================

This fault is typically caused by the limited quota of the account.

In an ExeML project, after the deployment is started, the model is automatically deployed as a real-time service. If the number of real-time services exceeds the quota limit, the model cannot be deployed as a service. In this case, an error message is displayed in the ExeML project, indicating that the real-time service deployment task fails to be submitted.

Troubleshooting
---------------

-  Method 1: Choose **Service Deployment** > **Real-time Services**. On the displayed page, delete services that are no longer used to release resources.
-  Method 2: If the deployed real-time service still needs to be used, you are advised to apply for a higher quota.
