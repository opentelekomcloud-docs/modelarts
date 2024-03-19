:original_name: modelarts_trouble_0045.html

.. _modelarts_trouble_0045:

Error Message "reason:Forbidden" Displayed in Logs
==================================================

Symptom
-------

When a training job accessed OBS, an error occurred.


.. figure:: /_static/images/en-us_image_0000001799338768.png
   :alt: **Figure 1** Error log

   **Figure 1** Error log

Possible Causes
---------------

The possible causes are as follows (see **Python > Troubleshooting > OBS Server-Side Error Codes** in *Object Storage Service SDK Reference*):

-  The OBS SDK version in the image is too early and needs to be upgraded.
-  The target account does not have the read-write permissions to the bucket.
-  The AK/SK is incorrectly configured in the environment.

Solution
--------

Check whether the target account has the read-write permissions to the bucket. If this issue is not caused by the permissions, submit a service ticket to OBS engineers to locate the fault and update the environment variables.

Summary and Suggestions
-----------------------

Before creating a training job, use the ModelArts development environment to debug the training code to maximally eliminate errors in code migration.
