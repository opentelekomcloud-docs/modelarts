:original_name: develop-modelarts-0097.html

.. _develop-modelarts-0097:

Viewing Training Job Logs
=========================

On the training job details page, you can preview logs, download logs, search for logs by keyword, and filter system logs in the log pane.

-  Previewing logs

   You can preview logs of each compute node, if multiple compute nodes are used, in the training log pane by choosing the target node from the drop-down list on the right.

   If a log file is oversized, the system displays only the latest logs in the log pane. To view all logs, click the link in the upper part of the log pane, which will direct you to a new page.


   .. figure:: /_static/images/en-us_image_0000001916629192.png
      :alt: **Figure 1** Viewing all logs

      **Figure 1** Viewing all logs

   .. note::

      -  If the total size of all logs exceeds 500 MB, the log page may be frozen. In this case, download the logs to view them locally.

      -  A log preview link can be accessed by anyone within one hour after it is generated. You can share the link with others.

         Ensure that no privacy information is contained in the logs. Otherwise, information leakage may occur.

-  Downloading logs

   Training logs are retained for only 30 days. To permanently store logs, click the download icon in the upper right corner of the log pane. You can download the logs of multiple compute nodes in a batch. You can also enable **Persistent Log Saving** and set a log path when you create a training job. In this way, the logs will be automatically stored in the specified OBS path.

   If a training job is created on an Ascend compute node, certain system logs cannot be downloaded in the training log pane. To obtain these logs, go to the **Job Log Path** you set when you created the training job.


   .. figure:: /_static/images/en-us_image_0000001916469920.png
      :alt: **Figure 2** Downloading logs

      **Figure 2** Downloading logs

-  Searching for logs by keyword

   In the upper right corner of the log pane, enter a keyword in the search box to search for logs, as shown in :ref:`Figure 3 <en-us_topic_0000001943975513__en-us_topic_0000001205728145_fig1676414594594>`.

   .. _en-us_topic_0000001943975513__en-us_topic_0000001205728145_fig1676414594594:

   .. figure:: /_static/images/en-us_image_0000001916629860.png
      :alt: **Figure 3** Searching for logs by keyword

      **Figure 3** Searching for logs by keyword

   The system will highlight the keyword and redirect you between search results. Only the logs loaded in the log pane can be searched for. If the logs are not fully displayed (see the message displayed on the page), obtain all the logs by downloading them or clicking the full log link and then search for the logs. On the page redirected by the full log link, press **Ctrl+F** to search for logs.

-  Filtering system logs


   .. figure:: /_static/images/en-us_image_0000001916630068.png
      :alt: **Figure 4** System logs

      **Figure 4** System logs

   If **System logs** is selected, system logs and user logs are displayed. If **System logs** is deselected, only user logs are displayed.
