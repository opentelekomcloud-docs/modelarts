:original_name: modelarts_trouble_0045.html

.. _modelarts_trouble_0045:

What Should I Do If Error "stat:403 reason:Forbidden" Is Displayed in Logs When a Training Job Accesses OBS
===========================================================================================================

Symptom
-------

When a training job accesses OBS, an error occurs.


.. figure:: /_static/images/en-us_image_0000002374847117.png
   :alt: **Figure 1** Error log

   **Figure 1** Error log

Possible Causes
---------------

The possible causes are as follows:

-  The OBS permission is incorrect. As a result, data cannot be read.

Solution
--------

Verify that OBS permissions are correctly assigned. If the problem persists, troubleshoot by following the instructions provided in "Why Can't I Access OBS (403 AccessDenied) After Being Granted with the OBS Access Permission?".

Summary and Suggestions
-----------------------

Before creating a training job, use the ModelArts development environment to debug the training code to maximally eliminate errors in code migration.

-  If an error occurred in OBS, identify the cause based on the error information, including the error code and message. For details about OBS error codes, see **Python > Troubleshooting > OBS Server-Side Error Codes** in *Object Storage Service SDK Reference*.
