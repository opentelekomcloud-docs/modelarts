:original_name: modelarts_trouble_0108.html

.. _modelarts_trouble_0108:

Detecting Training Job Suspension
=================================

Overview
--------

A training job may be suspended due to unknown reasons. If the suspension cannot be detected promptly, resources cannot be released, leading to a waste. To minimize resource cost and improve user experience, ModelArts provides suspension detection for training jobs. With this function, suspension can be automatically detected and displayed on the log details page. You can also enable notification so that you can be promptly notified of job suspension.

.. caution::

   -  Due to the limitation of :ref:`detection rules <en-us_topic_0000002374725637__en-us_topic_0000001279351401_section173451049121714>`, there is a certain error probability in suspension detection. If the suspension is caused by the logic of job code (for example, long-time sleep), ignore it.

.. _en-us_topic_0000002374725637__en-us_topic_0000001279351401_section173451049121714:

Detection Rules
---------------

Determine whether a job is suspended based on the monitored job process status and resource usage. A process is started to periodically monitor the changes of the two metrics.

-  Job process status: If the process I/O of a training job changes, the next detection period starts. If the process I/O of the job remains unchanged in multiple detection periods, the resource usage detection starts.
-  Resource usage: If the process I/O remains unchanged, the system collects the GPU usage within a certain period of time and determines whether the resource usage changes based on the variance and median of the GPU usage within the period. If the GPU usage is not changed, the job is suspended.

Constraints
-----------

Suspension can be detected only for training jobs that run on GPUs.

Procedure
---------

Suspension detection is automatically performed during job running. No additional configuration is required. After detecting that a job is suspended, the system displays a message on the training job details page, indicating that the job may be suspended. If you want to be notified of suspension (by SMS or email), enable event notification on the training job creation page.

Cases
-----

Common cases and solutions to training job suspension are as follows:

:ref:`Suspension in Data Copy <modelarts_trouble_0110>`

:ref:`Suspension Before Training <modelarts_trouble_0111>`

:ref:`Suspension During Training <modelarts_trouble_0112>`

:ref:`Suspension in the Last Training Epoch <modelarts_trouble_0113>`
