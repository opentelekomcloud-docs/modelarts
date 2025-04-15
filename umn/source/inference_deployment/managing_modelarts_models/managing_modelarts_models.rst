:original_name: inference-modelarts-0013.html

.. _inference-modelarts-0013:

Managing ModelArts Models
=========================

To facilitate source tracing and repeated model tuning, ModelArts provides the model version management function. You can manage models based on versions.

Prerequisites
-------------

A model has been created in ModelArts.

.. _en-us_topic_0000002268741853__en-us_topic_0171858290_section102881451161111:

Creating a New Version
----------------------

On the Model Management page, click **Create Version** in the **Operation** column of the target model. On the **Create Version** page, set the parameters. For details, see :ref:`Creating a Model <inference-modelarts-0004>`. Click **Create now**.

Deleting a Version
------------------

On the **Model Management** page, click the downward arrow on the left of the model name to expand an application version list. In the application version list, click **Delete** in the **Operation** column to delete the corresponding version.

.. note::

   If a service has been deployed for the model version, you need to delete the associated service before deleting the model version. A deleted version cannot be recovered. Exercise caution when performing this operation.

Deleting a Model
----------------

In the navigation pane, choose **Model Management (AI Applications)**. On the **Model Management** page, click **Delete** in the **Operation** column to delete the target model.

.. note::

   If a service has been deployed for the model version, you need to delete the associated service before deleting the model version. A deleted model cannot be recovered. Exercise caution when performing this operation.
