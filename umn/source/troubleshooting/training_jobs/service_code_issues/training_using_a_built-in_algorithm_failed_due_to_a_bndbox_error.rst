:original_name: modelarts_13_0041.html

.. _modelarts_13_0041:

Training Using a Built-in Algorithm Failed Due to a **bndbox** Error
====================================================================

Symptom
-------

When a training job is created using a built-in algorithm, the training failed with the following error message in the log:

.. code-block::

   KeyError: 'bndbox'

Possible Causes
---------------

Non-rectangles are used for labeling training sets. However, the built-in algorithm does not support datasets labeled by a non-rectangle.

Solution
--------

This issue can be resolved in either of the following ways:

-  Method 1: Use a common framework to develop a model that supports polygon-labeled datasets.
-  Method 2: Use rectangles to label the datasets. Then, start the training job again.
