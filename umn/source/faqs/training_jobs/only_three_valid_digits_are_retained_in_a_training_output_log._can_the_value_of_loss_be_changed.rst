:original_name: modelarts_21_0083.html

.. _modelarts_21_0083:

Only Three Valid Digits Are Retained in a Training Output Log. Can the Value of loss Be Changed?
================================================================================================

In a training job, only three valid digits are retained in a training output log. When the value of **loss** is too small, the value is displayed as **0.000**. Log content is as follows:

.. code-block::

   INFO:tensorflow:global_step/sec: 0.382191
   INFO:tensorflow:step: 81600(global step: 81600) sample/sec: 12.098 loss: 0.000
   INFO:tensorflow:global_step/sec: 0.382876
   INFO:tensorflow:step: 81700(global step: 81700) sample/sec: 12.298 loss: 0.000

Currently, the value of **loss** cannot be changed. You can multiply the value of **loss** by 1000 to avoid this problem.
