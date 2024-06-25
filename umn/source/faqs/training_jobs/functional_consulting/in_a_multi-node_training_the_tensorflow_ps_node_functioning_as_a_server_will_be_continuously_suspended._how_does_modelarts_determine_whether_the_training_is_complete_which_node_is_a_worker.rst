:original_name: modelarts_05_0382.html

.. _modelarts_05_0382:

In a Multi-Node Training, the TensorFlow PS Node Functioning as a Server Will Be Continuously Suspended. How Does ModelArts Determine Whether the Training Is Complete? Which Node Is a Worker?
===============================================================================================================================================================================================

In a TensorFlow-powered distributed training, the PS task and worker task are started. The worker task is a key task. ModelArts will use a process exit code of the worker task to determine whether the training job is complete.

A task name will be used to determine which node is a worker. A Volcano job is issued for training, which contains a PS task and a worker task. The startup commands of the two tasks are different. The hyperparameter **task_name** will be automatically generated, which is **ps** for the PS task and **worker** for the worker task.
