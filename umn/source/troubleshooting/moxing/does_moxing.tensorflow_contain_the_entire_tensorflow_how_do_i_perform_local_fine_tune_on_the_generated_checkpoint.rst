:original_name: modelarts_13_0027.html

.. _modelarts_13_0027:

Does moxing.tensorflow Contain the Entire TensorFlow? How Do I Perform Local Fine Tune on the Generated Checkpoint?
===================================================================================================================

Symptom
-------

When MoXing is used to train a model, **global_step** is placed in the Adam name range. The non-MoXing code does not contain the Adam name range. See :ref:`Figure 1 <en-us_topic_0000002043025108__fig934813253212>`. In the figure, **1** indicates MoXing code, and **2** indicates non-MoXing code.

.. _en-us_topic_0000002043025108__fig934813253212:

.. figure:: /_static/images/en-us_image_0000002043025280.png
   :alt: **Figure 1** Sample code

   **Figure 1** Sample code

Solution
--------

Fine tune is a process of using a model that is trained by others and your own data to train a new model. It is equivalent to using the several top layers of a model trained by others to extract shallow features, and then making the features fall into our own classification.

Generally, the accuracy of a newly trained model increases gradually from a very low value. However, fine tune allows you to obtain a better effect after a relatively small number of iterations. The advantage of fine tune is that it prevents you from training a model from scratch and improves training efficiency. Fine tune is a good choice when the data volume is not large.

All APIs contained in **moxing.tensorflow** have been optimized for TensorFlow. The actual APIs inside are the native APIs of TensorFlow.

If non-MoXing code does not contain the Adam name range, add the following content to non-MoXing code:

.. code-block::

   with tf.variable_scope("Adam"):

When adding code, you are advised to use **tf.train.get_or_create_global_step()** instead of **global_step**.
