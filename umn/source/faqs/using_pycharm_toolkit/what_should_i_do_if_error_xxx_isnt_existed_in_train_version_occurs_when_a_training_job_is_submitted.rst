:original_name: modelarts_15_0020.html

.. _modelarts_15_0020:

What Should I Do If Error "xxx isn't existed in train_version" Occurs When a Training Job Is Submitted?
=======================================================================================================

Symptom
-------

Error "xxx isn't existed in train_version" occurs when a training job is submitted. See the following figure.


.. figure:: /_static/images/en-us_image_0000002340730412.png
   :alt: **Figure 1** Error "xxx isn't existed in train_version"

   **Figure 1** Error "xxx isn't existed in train_version"

Possible Causes
---------------

The preceding error occurs because the user logs in to the ModelArts management console and deletes the training job after submitting the training job using PyCharm Toolkit.

PyCharm Toolkit records the training job IDs of ModelArts on the cloud. If you manually delete the job on the ModelArts management console, a message is displayed indicating that the job with the ID cannot be found when you submit the job locally.

Solution
--------

If you have deleted a job on the ModelArts management console, you also need to delete the local configuration from Toolkit. To delete the local configuration, click **Edit Training Configuration**, find the job name, click the minus sign in the upper right corner, and confirm the deletion.


.. figure:: /_static/images/en-us_image_0000002374848245.png
   :alt: **Figure 2** Deleting the local configuration

   **Figure 2** Deleting the local configuration

In the displayed confirmation dialog box, confirm the information and click **Yes** to delete the configuration. After the deletion, you can create a training job configuration and submit the training job.
