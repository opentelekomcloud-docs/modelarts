.. _modelarts_23_0189:

Viewing Monitoring Metrics
==========================

Scenario
--------

Cloud Eye on the cloud service platform monitors the status of ModelArts real-time services and model loads. You can obtain the monitoring metrics of each ModelArts real-time service and model loads on the management console. Monitored data requires a period of time for transmission and display. The status of ModelArts displayed on the Cloud Eye console is usually the status obtained 5 to 10 minutes before. You can view the monitored data of a newly created real-time service 5 to 10 minutes later.

Prerequisites
-------------

-  The ModelArts real-time service is running properly.

-  Alarm rules have been configured on the Cloud Eye page. For details, see :ref:`Setting Alarm Rules <modelarts_23_0188>`.
-  The real-time service has been properly running for at least 10 minutes.
-  The monitoring data and graphics are available for a new real-time service after the service runs for at least 10 minutes.

-  Cloud Eye does not display the metrics of a faulty or deleted real-time service. The monitoring metrics can be viewed after the real-time service starts or recovers.

Monitoring data is unavailable without alarm rules configured on Cloud Eye. For details, see :ref:`Setting Alarm Rules <modelarts_23_0188>`.

Procedure
---------

#. Log in to the management console.

#. Click **Service List**. Under **Management & Deployment**, click **Cloud Eye**.

#. In the left navigation pane, choose **Cloud Service Monitoring > ModelArts**.

#. View monitoring graphs.

   -  Viewing monitoring graphs of the real-time service: Click **View Graph** in the **Operation** column.
   -  Viewing monitoring graphs of the model loads: Click |image1| next to the target real-time service, and select **View Graph** from the drop-down list for model loads in the **Operation** column.

#. In the monitoring area, you can select a duration to view the monitoring data.

   You can view the monitoring data in the recent 1 hour, 3 hours, or 12 hours. To view the monitoring curve of a longer time range, click |image2| to enlarge the graph.

.. |image1| image:: /_static/images/en-us_image_0000001110920964.png

.. |image2| image:: /_static/images/en-us_image_0000001110761062.png

