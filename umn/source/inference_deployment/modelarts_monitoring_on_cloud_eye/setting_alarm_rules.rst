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

-  A ModelArts real-time service has been created.
-  ModelArts monitoring has been enabled on Cloud Eye. To do so, log in to the Cloud Eye console. On the Cloud Eye page, click **Custom Monitoring**. Then, enable ModelArts monitoring as prompted.

Procedure
---------

Set an alarm rule in any of the following ways:

-  Set an alarm rule for all ModelArts services.
-  Set an alarm rule for a ModelArts service.
-  Set an alarm rule for a model version.
-  Set an alarm rule for a metric of a service or model version.

Method 1: Setting an Alarm Rule for All ModelArts Services
----------------------------------------------------------

#. Log in to the management console.
#. In the **Service List**, click **Cloud Eye** under **Management & Governance**.
#. In the navigation pane on the left, choose **Alarm Management** > **Alarm Rules** and click **Create Alarm Rule**.
#. On the **Create Alarm Rule** page, set **Resource Type** to **ModelArts**, **Dimension** to **Service**, and **Method** to **Configure manually**, and set alarm policies. Then, confirm settings and click **Create**.

Method 2: Setting an Alarm Rule for a Single Service
----------------------------------------------------

#. Log in to the management console.
#. In the **Service List**, click **Cloud Eye** under **Management & Governance**.
#. In the navigation pane, choose **Cloud Service Monitoring > ModelArts**.
#. Locate a real-time service for which you want to create an alarm rule and click **Create Alarm Rule** in the **Operation** column.
#. On the **Create Alarm Rule** page, create an alarm rule for ModelArts real-time services and models as prompted.

Method 3: Setting an Alarm Rule for a Model Version
---------------------------------------------------

#. Log in to the management console.
#. In the **Service List**, click **Cloud Eye** under **Management & Governance**.
#. In the navigation pane, choose **Cloud Service Monitoring > ModelArts**.
#. Click the down arrow next to the target real-time service name. Then, click **Create Alarm Rule** in the **Operation** column of the target version.
#. On the **Create Alarm Rule** page, create an alarm rule for model loads as prompted.

Method 4: Setting an Alarm Rule for a Metric of a Service or Model Version
--------------------------------------------------------------------------

#. Log in to the management console.
#. In the **Service List**, click **Cloud Eye** under **Management & Governance**.
#. In the navigation pane, choose **Cloud Service Monitoring > ModelArts**.
#. Click the down arrow next to the target real-time service name. Then, click the target version and view alarm rule details.
#. On the alarm rule details page, click the plus sign (+) in the upper right corner of a metric and set an alarm rule for the metric.
