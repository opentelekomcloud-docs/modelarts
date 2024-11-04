:original_name: inference-modelarts-0013.html

.. _inference-modelarts-0013:

Managing AI Applications
========================

To facilitate source tracing and repeated AI application tuning, ModelArts provides the AI application version management function. You can manage models based on versions.

Prerequisites
-------------

An AI application has been created in ModelArts.

.. _en-us_topic_0000002043024844__en-us_topic_0171858290_section102881451161111:

Creating a New Version
----------------------

On the **AI Application Management** > **AI Applications** page, click **Create Version** in the **Operation** column of the target AI application. On the **Create Version** page, set the parameters. For details, see :ref:`Creating an AI Application <inference-modelarts-0004>`. Click **Create now**.

Deleting a Version
------------------

On the **AI Application Management > AI Applications** page, click the downward arrow on the left of the AI application name to expand an application version list. In the application version list, click **Delete** in the **Operation** column to delete the corresponding version.

.. note::

   If a service has been deployed for the AI application version, you need to delete the associated service before deleting the AI application version. A deleted version cannot be recovered. Exercise caution when performing this operation.

Deleting an AI Application
--------------------------

In the navigation pane, choose **AI Application Management** > **AI Applications**. On the **AI Applications** page, click **Delete** in the **Operation** column to delete the target AI application.

.. note::

   If a service has been deployed for the AI application version, you need to delete the associated service before deleting the AI application version. A deleted AI application cannot be recovered. Exercise caution when performing this operation.
