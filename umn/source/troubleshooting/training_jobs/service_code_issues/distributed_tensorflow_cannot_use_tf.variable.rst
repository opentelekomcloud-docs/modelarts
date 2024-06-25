:original_name: modelarts_13_0016.html

.. _modelarts_13_0016:

Distributed Tensorflow Cannot Use **tf.variable**
=================================================

Symptom
-------

The following error occurs when **tf.variable** is used across multiple machines and multiple GPUs: **WARNING:tensorflow:Gradient is None for variable:v0/tower_0/UNET_v7/sub_pixel/Variable:0.Make sure this variable is used in loss computation**


.. figure:: /_static/images/en-us_image_0000001943968425.png
   :alt: **Figure 1** Distributed Tensorflow unavailable

   **Figure 1** Distributed Tensorflow unavailable

Possible Cause
--------------

Distributed TensorFlow needs to use **tf.get_variable** instead of **tf.variable**.

Solution
--------

Replace **tf.variable** in the boot file with **tf.get_variable**.
