:original_name: inference-modelarts-0087.html

.. _inference-modelarts-0087:

Upgrading a Service
===================

For a deployed service, you can modify its basic information to match service changes and change the model version to upgrade it.

You can modify the basic information about a service in either of the following ways:

:ref:`Method 1: Modify Service Information on the Service Management Page <en-us_topic_0000002374850185__en-us_topic_0172547189_section6987155265816>`

:ref:`Method 2: Modify Service Information on the Service Details Page <en-us_topic_0000002374850185__en-us_topic_0172547189_section12604201617210>`

Prerequisites
-------------

The service has been deployed. The service in the **Deploying** state cannot be upgraded by modifying the service information.

Constraints
-----------

-  Improper upgrade operations will interrupt service running during the upgrade. Therefore, exercise caution when performing this operation.
-  ModelArts supports hitless rolling upgrade of real-time services in some scenarios. Before upgrade, prepare for it and confirm the prerequisites.

   .. table:: **Table 1** Scenarios for hitless rolling upgrade

      +----------------------------------------+------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | Meta Model Source for Creating a model | Using a Public Resource Pool | Using a Dedicated Resource Pool                                                                                                         |
      +========================================+==============================+=========================================================================================================================================+
      | Training job                           | Not supported                | Not supported                                                                                                                           |
      +----------------------------------------+------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | Container image                        | Not supported                | Supported. The custom image for creating a model must meet :ref:`Custom Image Specifications for Creating a Model <modelarts_23_0219>`. |
      +----------------------------------------+------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | OBS                                    | Not supported                | Not supported                                                                                                                           |
      +----------------------------------------+------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+

.. _en-us_topic_0000002374850185__en-us_topic_0172547189_section6987155265816:

Method 1: Modify Service Information on the Service Management Page
-------------------------------------------------------------------

#. Log in to the ModelArts management console and choose **Service Deployment** from the left navigation pane. Go to the service management page of the target service.

#. In the service list, click **Modify** in the **Operation** column of the target service, modify basic service information, and submit the modification task as prompted.

   When some parameters are modified, the system automatically restarts the service for the modification to take effect. When you submit a service modification task, if a restart is required, a dialog box will be displayed.

   -  For details about the real-time service parameters, see :ref:`Deploying as a Real-Time Service <inference-modelarts-0018>`.
   -  For details about the batch service parameters, see :ref:`Deploying as a Batch Service <inference-modelarts-0040>`.

.. _en-us_topic_0000002374850185__en-us_topic_0172547189_section12604201617210:

Method 2: Modify Service Information on the Service Details Page
----------------------------------------------------------------

#. Log in to the ModelArts management console and choose **Service Deployment** from the left navigation pane. Go to the service management page of the target service.

#. Click the name of the target service. The service details page is displayed.

#. Click **Modify** in the upper right corner of the page, modify the service details, and submit the modification task as prompted.

   When some parameters are modified, the system automatically restarts the service for the modification to take effect. When you submit a service modification task, if a restart is required, a dialog box will be displayed.

   -  For details about the real-time service parameters, see :ref:`Deploying as a Real-Time Service <inference-modelarts-0018>`.
   -  For details about the batch service parameters, see :ref:`Deploying as a Batch Service <inference-modelarts-0040>`.
