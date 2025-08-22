:original_name: modelarts_05_0363.html

.. _modelarts_05_0363:

Why Is a Training Job Always Queuing?
=====================================

First in first out (FIFO) applies to training jobs. Subsequent jobs can be executed only after the preceding job is complete. This may lead to starvation of small jobs.

.. note::

   Job starvation is as follows: For example, a 64-card training job is queuing, and a 1-card training job follows the 64-card one. The 1-card training job can be executed only after the resources of 64 cards are idle. Even if the resources of 30 cards are available, the 1-card training job cannot be executed.

-  If the resource pool is a public one, the job is generally pending because resources are occupied other users. Try to take the following measures:

   -  If a free flavor was used, change it to a charged one. Few resources are provided for free flavors, leading to a high queuing probability.
   -  To minimize queuing, select flavors with the smallest number of cards possible. This reduces the likelihood of queuing significantly. For example, the probability of queuing when selecting a 1-card flavor is much less than that of queuing when selecting an 8-card flavor.
   -  Switch to another region.
   -  If resources will be used for a long term, purchase a dedicated resource pool.

-  If a dedicated resource pool is used, perform the following operations:

   #. Check whether other jobs (including inference jobs, training jobs, and development environment jobs) are running in the dedicated resource pool.

      On the **Overview** page, you can go to the details page of the running jobs or instances to check whether the dedicated resource pool is used. You can stop them based on your needs to release resources.

   #. Click the dedicated resource pool to go to the details page and view the job list.

      If other jobs are waiting in the queue, the new job must also join the queue.

   #. Check whether resources are fragmented.

      For example, the cluster has two nodes, and there are four idle cards on each node. However, your job requires eight cards on one node. In this case, the idle resources cannot be allocated to your job.
