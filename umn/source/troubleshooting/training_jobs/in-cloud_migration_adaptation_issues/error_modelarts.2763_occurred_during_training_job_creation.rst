:original_name: modelarts_13_0159.html

.. _modelarts_13_0159:

Error ModelArts.2763 Occurred During Training Job Creation
==========================================================

Symptom
-------

When a training job is created, error code ModelArts.2763 is displayed, indicating that the selected instance is invalid.

Possible Causes
---------------

The selected training flavor does not match the algorithm.

Solution
--------

#. Check the training resource flavor configured in the algorithm code.
#. Check whether the resource flavor selected during training job creation is correct. If not, create a training job with the correct resource flavor.
