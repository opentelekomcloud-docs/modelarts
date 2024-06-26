:original_name: modelarts_23_0071.html

.. _modelarts_23_0071:

Upgrading a Service
===================

For a deployed service, you can modify its basic information to match service changes and upgrade it. You can modify the basic information about a service in either of the following ways:

:ref:`Method 1: Modify Service Information on the Service Management Page <modelarts_23_0071__en-us_topic_0172547189_section6987155265816>`

:ref:`Method 2: Modify Service Information on the Service Details Page <modelarts_23_0071__en-us_topic_0172547189_section12604201617210>`

Prerequisites
-------------

A service has been deployed.

Constraints
-----------

-  Improper upgrade operations will interrupt service running during the upgrade. Therefore, exercise caution when performing this operation.
-  ModelArts supports hitless rolling upgrade of real-time services in some scenarios. Before upgrade, prepare for it and confirm the prerequisites.

   .. table:: **Table 1** Scenarios for hitless rolling upgrade

      +--------------------------------------------------+------------------------------+------------------------------------------------------------------------+
      | Meta Model Source for Creating an AI Application | Using a Public Resource Pool | Using a Dedicated Resource Pool                                        |
      +==================================================+==============================+========================================================================+
      | Training job                                     | Not supported                | Not supported                                                          |
      +--------------------------------------------------+------------------------------+------------------------------------------------------------------------+
      | Template                                         | Not supported                | Not supported                                                          |
      +--------------------------------------------------+------------------------------+------------------------------------------------------------------------+
      | Container image                                  | Not supported                | Supported. The custom image for creating an AI application must meet . |
      +--------------------------------------------------+------------------------------+------------------------------------------------------------------------+
      | OBS                                              | Not supported                | Not supported                                                          |
      +--------------------------------------------------+------------------------------+------------------------------------------------------------------------+

.. _modelarts_23_0071__en-us_topic_0172547189_section6987155265816:

Method 1: Modify Service Information on the Service Management Page
-------------------------------------------------------------------

#. Log in to the ModelArts management console and choose **Service Deployment** from the left navigation pane. Go to the service management page of the target service.
#. In the service list, click **Modify** in the **Operation** column of the target service, modify basic service information, and click **OK**.

   -  For details about the real-time service parameters, see :ref:`Deploying a Model as a Real-Time Service <modelarts_23_0060>`.
   -  For details about the batch service parameters, see :ref:`Deploying a Model as a Batch Service <modelarts_23_0066>`.

   .. note::

      Services in the **Deploying** status cannot be modified.

.. _modelarts_23_0071__en-us_topic_0172547189_section12604201617210:

Method 2: Modify Service Information on the Service Details Page
----------------------------------------------------------------

#. Log in to the ModelArts management console and choose **Service Deployment** from the left navigation pane. Go to the service management page of the target service.
#. Click the name of the target service. The service details page is displayed.
#. Click **Modify** in the upper right corner of the page, modify the service details, and click **OK**.

   -  For details about the real-time service parameters, see :ref:`Deploying a Model as a Real-Time Service <modelarts_23_0060>`.
   -  For details about the batch service parameters, see :ref:`Deploying a Model as a Batch Service <modelarts_23_0066>`.
