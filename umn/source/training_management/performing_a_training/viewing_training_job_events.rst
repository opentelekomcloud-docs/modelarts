:original_name: develop-modelarts-0092.html

.. _develop-modelarts-0092:

Viewing Training Job Events
===========================

Any key event of a training job will be recorded at the backend after the training job is displayed for you. You can check events on the training job details page.

This helps you better understand the running process of a training job and locate faults more accurately when a task exception occurs. The following job events are supported:

-  Training job created.
-  Training job failures:
-  Preparations timed out. The possible cause is that the cross-region algorithm synchronization or creating shared storage timed out.
-  The training job is queuing and awaiting resource allocation.
-  Failed to be queued.
-  The training job starts to run.
-  Training job executed.
-  Failed to run the training job.
-  The training job is preempted.
-  The system detects that your training job may be suspended. Go to the job details page to view the cause and handle the issue.
-  The training job has been restarted.
-  The training job has been manually stopped.
-  The training job has been stopped. (Maximum running duration: 1 hour)
-  The training job has been stopped. (Maximum running duration: 3 hours)
-  The training job has been manually deleted.
-  Billing information synchronized.
-  [worker-0] The training environment is being pre-checked.
-  [worker-0] [Duration: second] Pre-check completed.
-  [worker-0] [Duration: second] Pre-check failed. Error: xxx
-  [worker-0] [Duration: second] Pre-check failed. Error: xxx
-  [worker-0] The training code is being downloaded.
-  [worker-0] [Duration: second] Training code downloaded.
-  [worker-0] [Duration: second] Failed to download the training code. Failure cause:
-  [worker-0] The training input is being downloaded.
-  [worker-0] [Duration: second] Training input (parameter: xxx) downloaded.
-  [worker-0] [Duration: second] Failed to download the training input (parameter: xxx). Failure cause:
-  [worker-0] Python dependency packages are being installed. Import the following files:
-  [worker-0] [Duration: second] Python dependency packages installed. Import the following files:
-  [worker-0] The training job starts to run.
-  [worker-0] Training job executed.
-  [worker-0] The training input is being uploaded.
-  [worker-0] [Duration: second] Training output (parameter: xxx) uploaded.

During the training process, key events can be manually or automatically refreshed.

Procedure
---------

#. In the navigation pane of the ModelArts management console, choose **Training Management** > **Training Jobs**. In the training job list, click a job name.
#. Click **Events** to view events.
