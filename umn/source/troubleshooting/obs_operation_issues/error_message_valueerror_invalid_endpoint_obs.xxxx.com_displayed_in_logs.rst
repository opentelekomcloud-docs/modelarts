:original_name: modelarts_trouble_0048.html

.. _modelarts_trouble_0048:

Error Message "ValueError: Invalid endpoint: obs.xxxx.com" Displayed in Logs
============================================================================

Symptom
-------

When TensorBoard is used to directly write data in an OBS path for a training job, an error similar to the following is displayed.


.. figure:: /_static/images/en-us_image_0000001846137705.png
   :alt: **Figure 1** Error log

   **Figure 1** Error log

Possible Causes
---------------

The possible causes are as follows:

It is unstable to directly write data into the TensorBoard file in OBS.

Solution
--------

Locally write data and then copy it back to OBS.

Summary and Suggestions
-----------------------

Before creating a training job, use the ModelArts development environment to debug the training code to maximally eliminate errors in code migration.
