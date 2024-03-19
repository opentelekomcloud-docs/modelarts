:original_name: modelarts_23_0401.html

.. _modelarts_23_0401:

Training Log Details
====================

On the training job details page, you can preview logs, download logs, search for logs by keyword, and identify training faults in the log pane.

-  Preview logs.

   You can preview logs of each compute node, if multiple compute nodes are used, in the training log pane by choosing the target node from the drop-down list on the right.

   If a log file is oversized, the system displays only the latest logs in the log pane. To view all logs, click the link in the upper part of the log pane, which will direct you to a new page.


   .. figure:: /_static/images/en-us_image_0000001805560062.png
      :alt: **Figure 1** Viewing all logs

      **Figure 1** Viewing all logs

   .. note::

      -  If the total size of all logs exceeds 500 MB, the log page may be frozen. In this case, download the logs to view them locally.

      -  A log preview link can be accessed by anyone within one hour after it is generated. You can share the link with others.

         Ensure that no privacy information is contained in the logs. Otherwise, information leakage may occur.

-  Download logs.

   Training logs are retained for only 30 days. To permanently store logs, click the download icon in the upper right corner of the log pane. You can download the logs of multiple compute nodes in a batch. You can also enable **Persistent Log Saving** and set a log path when you :ref:`create a training job <modelarts_23_0286>`. In this way, the logs will be automatically stored in the specified OBS path.

   If a training job is created on an Ascend compute node, certain system logs cannot be downloaded in the training log pane. To obtain these logs, go to the **Job Log Path** you set when you created the training job.


   .. figure:: /_static/images/en-us_image_0000001805560310.png
      :alt: **Figure 2** Downloading logs

      **Figure 2** Downloading logs

-  Search for logs by keyword.

   In the upper right corner of the log pane, enter a keyword in the search box to search for logs. The system will highlight the keyword and redirect you between search results.


   .. figure:: /_static/images/en-us_image_0000001852079633.png
      :alt: **Figure 3** Searching for logs

      **Figure 3** Searching for logs

   .. note::

      -  Only the logs loaded in the log pane can be searched for. If the logs are not fully displayed (see the message displayed on the page), obtain all the logs by downloading them or clicking the full log link and then search for the logs.
      -  On the page redirected by the full log link, press **Ctrl+F** to search for logs.

-  Identify training faults.

   If your training job failed, the system automatically identifies the fault and displays a message on the page. The message consists of possible causes, recommended solutions, and error logs (marked in red). Recommended solutions are as follows:

   Solution 1: A troubleshooting document is provided for you to follow.

   Solution 2: Rebuild the training job and run it again. If the fault persists, submit a service ticket.

   Solution 3: Submit a service ticket.

   .. note::

      -  The system analyzes and provides troubleshooting suggestions for common training errors.
      -  The possible causes are for reference only.
      -  If the provided solutions cannot rectify your fault, you can submit a service ticket for technical support.
      -  For a distributed job, only the analysis result of the current node is displayed. To obtain the failure cause of a training job, check the analysis results of all nodes used by the training job.

Training Platform Logs
----------------------

.. code-block::

   Example: modelarts-job-9ccf15f2-6610-42f9-ab99-059ba049a41e-worker-0.log
   Unified log format: modelarts-job-[job id]-[task id].log

In the preceding example, *task id* is the node ID of a distributed job. If only one node is used, *task id* defaults to **worker-0**.

**training log** includes the logs for **pip-requirement.txt**, **ma-pre-start**, **davincirun**, training process, and ModelArts.

-  **ModelArts logs**

   Type 1: [ModelArts Service Log] xxx

   .. code-block::

      [ModelArts Service Log][init] download code_url: s3://dgg-test-user/ascend910-test-cases/mindspore/lenet/

   Type 2: time="xxx" level="xxx" msg="xxx" file="xxx" Command=xxx Component=xxx Platform=xxx

   .. code-block::

      time="2021-07-26T19:24:11+08:00" level=info msg="start the periodic upload task, upload period = 5 seconds " file="upload.go:46" Command=obs/upload Component=ma-training-toolkit Platform=ModelArts-Service

   Only one training log file is generated for a single-node job. ModelArts logs are used by O&M personnel to locate service faults. If the ModelArts logs are not involved, use the preceding rules to filter out these logs.

-  **proc log**

   **proc log** is a redirection file of single-node training logs, helping you quickly obtain logs of a compute node.

   .. code-block::

      Example: modelarts-job-9b43aba3-ed9c-48c1-9f5e-2d61d20dce65-proc-rank-6-device-6.txt
      Log file format: [modelarts-job-uuid]-proc-rank-[rank id]-device-[device logic id].txt

   In the preceding example, *device id* is the device ID in numerical sequence.
