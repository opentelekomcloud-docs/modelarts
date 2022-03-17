Viewing Job Details
===================

After a training job finishes, you can manage the training job versions and check whether the training result of the job is satisfactory by viewing the `job details <#training-job-details>`__.

Training Job Details
--------------------

In the left navigation pane of the ModelArts management console, choose **Training Management** > **Training Jobs** to switch to the **Training Jobs** page. In the training job list, click a job name to view the job details.

`Table 1 <#modelarts230048enustopic0171858286table43451384323>`__ lists parameters of the training job of each version.



.. _modelarts230048enustopic0171858286table43451384323:

.. table:: **Table 1** Training job details

   +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Description                                                                                                                                                                                                                        |
   +=================+====================================================================================================================================================================================================================================+
   | Version         | Version of a training job, which is automatically defined by the system, for example, **V0001** and **V0002**.                                                                                                                     |
   +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Status          | Status of a training job,                                                                                                                                                                                                          |
   +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Duration        | Running duration of a training job                                                                                                                                                                                                 |
   +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Configurations  | Details about the parameters of the current training job version                                                                                                                                                                   |
   +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Logs            | Logs of the current training job version. If you set **Log Output Path** when creating a training job, you can click the download button on the **Logs** tab page to download the logs stored in the OBS bucket to the local host. |
   +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Resource Usages | Usage of resources of the current training version, including the CPU, GPU, and memory.                                                                                                                                            |
   +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+


