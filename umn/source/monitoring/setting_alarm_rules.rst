:original_name: modelarts_23_0188.html

.. _modelarts_23_0188:

Setting Alarm Rules
===================

Scenario
--------

Setting alarm rules allows you to customize the monitored objects and notification policies so that you can know the status of ModelArts real-time services and models in a timely manner.

An alarm rule includes the alarm rule name, monitored object, metric, threshold, monitoring interval, and whether to send a notification. This section describes how to set alarm rules for ModelArts services and models.

.. note::

   Only real-time services in the **Running** status can be interconnected with CES.

Prerequisites
-------------

You have created a ModelArts real-time service.

Procedure
---------

#. Log in to the management console.
#. Click **Service List**. Under **Management & Deployment**, click **Cloud Eye**.
#. On the Cloud Eye page, click **Custom Monitoring**. Then, enable ModelArts monitoring as prompted.
#. In the left navigation pane, choose **Cloud Service Monitoring > ModelArts**.
#. Select a real-time service for which you want to create an alarm rule and click **Create Alarm Rule** in the **Operation** column.
#. On the **Create Alarm Rule** page, create an alarm rule for ModelArts real-time services and models as prompted.
#. After the setting is complete, click **Create**. When an alarm that meets the rule is generated, the system automatically sends a notification.
