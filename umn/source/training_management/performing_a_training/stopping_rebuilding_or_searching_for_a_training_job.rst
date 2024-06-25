:original_name: develop-modelarts-0017.html

.. _develop-modelarts-0017:

Stopping, Rebuilding, or Searching for a Training Job
=====================================================

Save As Algorithm
-----------------

To modify the algorithm of a training job, click **Save As Algorithm** in the upper right corner of the training job details page.

On the **Algorithms** page, the algorithm parameters for the last training job are automatically set. You can modify the settings.

.. note::

   This function is not supported for algorithms subscribed in AI Hub.

Stopping a Training Job
-----------------------

In the training job list, click **Stop** in the **Operation** column of a training job that is in creating, pending, or running state to stop the job.

A training job in completed, failed, terminated, or abnormal state cannot be stopped.

Rebuilding a Training Job
-------------------------

If you are not satisfied with a created training job, click **Rebuild** in the **Operation** column to rebuild it. The page for creating a training job is displayed. On this page, the parameter settings for the previous training job are automatically retained. You only need to modify certain parameter settings.

Searching for a Training Job
----------------------------

If you log in to ModelArts using an IAM account, all training jobs under this account are displayed in the training job list. To quickly search for a training job, use the following methods:

Method: Enable **Display Only My Instances**. Then, only jobs created under the current IAM account are displayed in the training job list.

Method: Search for a training job by job name.

Method: Search for jobs by name, ID, job type, status, creation time, algorithm, and resource pool.
