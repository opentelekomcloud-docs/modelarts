:original_name: modelarts_15_0021.html

.. _modelarts_15_0021:

What Should I Do If an Error Occurs When I Submit a Training Job?
=================================================================

When a training job is running, the "Invalid OBS path" error is reported.


.. figure:: /_static/images/en-us_image_0000001910018786.png
   :alt: **Figure 1** "Invalid OBS path" error

   **Figure 1** "Invalid OBS path" error

To locate the fault, perform the following operations:

-  If you are using ModelArts for the first time, log in to the ModelArts management console and complete access authorization configuration. The agency authorization mode is recommended. After the global configuration is complete, submit the job again.
-  Check whether the configured **Data Path in OBS** exists and whether data files exist in the directory. If the directory does not exist, create a directory on OBS and upload the training data to the directory.
