:original_name: modelarts_trouble_0112.html

.. _modelarts_trouble_0112:

Suspension During Training
==========================

Symptom 1
---------

According to the logs of the nodes on which a training job runs, an error occurred on a node but the job did not exit, leading to the job suspension.

Solution 1
----------

Check the error cause and rectify the fault.

Symptom 2
---------

The job is stuck in sync-batch-norm or the training speed is lowered down. If sync-batch-norm is enabled for PyTorch, the training speed is lowered down because all node data must be synchronized on each batch normalization layer in every iteration, which leads to heavy communication traffic.

|image1|

Solution 2
----------

Disable sync-batch-norm, or upgrade the PyTorch version to 1.10.

Symptom 3
---------

The job is stuck in TensorBoard.

|image2|

Solution 3
----------

Set a local path for storage, for example, **cache/tensorboard**. Do not store data in OBS.

Symptom 4
---------

When PyTorch dataloader is used to read data, the job is stuck in data reading, and logs stop to update.

|image3|

Solution 4
----------

When using dataloader to read data, set **num_work** to a small value.

|image4|

.. |image1| image:: /_static/images/en-us_image_0000002268819401.jpg
.. |image2| image:: /_static/images/en-us_image_0000002268819361.jpg
.. |image3| image:: /_static/images/en-us_image_0000002233900004.jpg
.. |image4| image:: /_static/images/en-us_image_0000002233740216.jpg
