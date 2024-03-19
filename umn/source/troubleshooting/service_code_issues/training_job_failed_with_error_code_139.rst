:original_name: modelarts_trouble_0039.html

.. _modelarts_trouble_0039:

Training Job Failed with Error Code 139
=======================================

Symptom
-------

The training job failed, and error code 139 is returned.

Possible Causes
---------------

The possible causes are as follows:

-  Certain pip packages in the pip source have been updated, leading to data incompatibility. For example, an error occurs when the transformers package is imported after the package update.
-  The user code has a bug, leading to memory overwriting or unauthorized memory access.
-  An unknown system error occurs. In this case, create the training job again. If the fault persists, submit a service ticket.

Solution
--------

#. If the training job succeeded before and no modification has been made, compare the logs in the two cases and check whether any dependency package has been updated in the pip source.
#. Use the local PyCharm to remotely connect to the notebook for debugging.
#. If the fault persists, contact technical support engineers.

Summary and Suggestions
-----------------------

Before creating a training job, use the ModelArts development environment to debug the training code to maximally eliminate errors in code migration.
