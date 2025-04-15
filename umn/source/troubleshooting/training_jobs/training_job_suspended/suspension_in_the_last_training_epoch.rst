:original_name: modelarts_trouble_0113.html

.. _modelarts_trouble_0113:

Suspension in the Last Training Epoch
=====================================

Symptom
-------

Logs showed that an error occurred in split data. As a result, processes are in different epochs, and uncompleted processes are suspended because they do not receive response from other processes. As shown in the following figure, some processes are in epoch 48 while others are in epoch 49 at the same time.

|image1|

Solution
--------

Ensure that all processes are in the same epoch.

.. |image1| image:: /_static/images/en-us_image_0000002233740904.png
