:original_name: modelarts_13_0211.html

.. _modelarts_13_0211:

Restrictions on the Size of an Image for Importing a Model
==========================================================

Symptom
-------

When an imported model is used to deploy a service, the system displays a message indicating that the idle disk space is insufficient for service deployment.

Possible Causes
---------------

ModelArts uses containers for deploying services. There are size limitations during container runtime. If the size of your model file, custom file, or system file exceeds the Docker size, a message will be displayed, indicating that the image space is insufficient.

Solution
--------

Ensure the size of the current model file is not greater than 20 GB and that of the custom image is not greater than 30 GB.
