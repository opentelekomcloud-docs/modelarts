:original_name: modelarts_23_0251.html

.. _modelarts_23_0251:

Viewing Audit Logs
==================

After CTS is enabled, CTS starts recording operations related to ModelArts. The CTS management console stores the last seven days of operation records. This section describes how to query operation records of the last seven days on the CTS management console.

Procedure
---------

#. Log in to the CTS management console.

#. Click |image1| in the upper left corner of the page and select a region.

#. In the left navigation pane, click **Trace List**.

#. Specify the filter criteria used for querying traces. The following four filter criteria are available:

   -  **Trace Source**, **Resource Type**, and **Search By**

      Select a filter criterion from the drop-down list.

      If you select **Trace name** for **Search By**, you need to select a specific trace name.

      If you select **Resource ID** for **Search By**, you need to enter a specific resource ID.

      If you select **Resource name** for **Search By**, you need to select or enter a specific resource name.

   -  **Operator**: Select a specific operator (a user rather than an account).

   -  **Trace Status**: Available options include **All trace statuses**, **normal**, **warning**, and **incident**. You can only select one of them.

   -  **Time Range**: You can view traces generated during any time range of the last seven days.

#. Click |image2| on the left of a trace to expand its details.

#. Click **View Trace** in the **Operation** column. In the displayed **View Trace** dialog box, the trace structure details are displayed.

   For details about the key fields in the CTS trace structure, see `Cloud Trace Service User Guide <https://docs.otc.t-systems.com/en-us/usermanual/cts/en-us_topic_0030579718.html>`__.

.. |image1| image:: /_static/images/en-us_image_0000001157080769.png

.. |image2| image:: /_static/images/en-us_image_0000001157080767.png

