:original_name: modelarts_01_0023.html

.. _modelarts_01_0023:

What Are the Events and Their Types for a Service?
==================================================

During the whole lifecycle of a service, every key event is automatically recorded. You can view the events on the details page of the service at any time.

The following table lists the events, based on which you can locate faults occurred during service deployment and running.

+----------+------------------------------------------------------------------------+
| Type     | Event (*xxx* should be replaced with the actual value.)                |
+----------+------------------------------------------------------------------------+
| Normal   | The service starts to deploy.                                          |
+----------+------------------------------------------------------------------------+
| Abnormal | Insufficient resources. Wait until idle resources are sufficient.      |
+----------+------------------------------------------------------------------------+
| Normal   | The image starts to create.                                            |
+----------+------------------------------------------------------------------------+
| Abnormal | Failed to create model image **xxx**. For details, see logs *:\\nxxx*. |
+----------+------------------------------------------------------------------------+
| Abnormal | Failed to create the image.                                            |
+----------+------------------------------------------------------------------------+
| Normal   | The image created.                                                     |
+----------+------------------------------------------------------------------------+
| Abnormal | Service *xxx* failed. Error: *xxx*                                     |
+----------+------------------------------------------------------------------------+
| Abnormal | Failed to update the service. Perform a rollback.                      |
+----------+------------------------------------------------------------------------+
| Normal   | The service is being updated.                                          |
+----------+------------------------------------------------------------------------+
| Normal   | The service is being started.                                          |
+----------+------------------------------------------------------------------------+
| Normal   | The service is being stopped.                                          |
+----------+------------------------------------------------------------------------+
| Normal   | The service has been stopped.                                          |
+----------+------------------------------------------------------------------------+
| Normal   | Auto stop has been disabled.                                           |
+----------+------------------------------------------------------------------------+
| Normal   | Auto stop has been enabled. The service will stop after *x*\ s.        |
+----------+------------------------------------------------------------------------+
| Normal   | The service stops when the auto stop time expires.                     |
+----------+------------------------------------------------------------------------+
| Abnormal | The service is stopped because the quota exceeds the upper limit.      |
+----------+------------------------------------------------------------------------+
| Abnormal | Failed to automatically stop the service. Error: *xxx*                 |
+----------+------------------------------------------------------------------------+
| Normal   | Service instances deleted from resource pool *xxx*.                    |
+----------+------------------------------------------------------------------------+
| Normal   | Service instances stopped in resource pool *xxx*.                      |
+----------+------------------------------------------------------------------------+
| Abnormal | The batch service failed. Try again later. Error: *xxx*                |
+----------+------------------------------------------------------------------------+
| Normal   | The service has been executed.                                         |
+----------+------------------------------------------------------------------------+
| Abnormal | Failed to stop the service. Error: *xxx*                               |
+----------+------------------------------------------------------------------------+
| Normal   | The subscription license *xxx* is to expire.                           |
+----------+------------------------------------------------------------------------+
| Normal   | Service *xxx* started.                                                 |
+----------+------------------------------------------------------------------------+
| Abnormal | Failed to start service *xxx*.                                         |
+----------+------------------------------------------------------------------------+
| Abnormal | Service deployment timed out. Error: *xxx*                             |
+----------+------------------------------------------------------------------------+
| Normal   | Failed to update the service. The update has been rolled back.         |
+----------+------------------------------------------------------------------------+
| Abnormal | Failed to update the service. The rollback failed.                     |
+----------+------------------------------------------------------------------------+

During service deployment and running, key events can both be manually and automatically refreshed.

Viewing Events
--------------

#. In the left navigation pane of the ModelArts management console, choose **Service Deployment** > **Real-Time Services** or **Batch Services** or **Edge Services**. In the service list, click the name or ID of the target service to go to its details page.
#. View the events on the **Events** tab page.
