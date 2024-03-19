:original_name: modelarts_trouble_0059.html

.. _modelarts_trouble_0059:

Error Message "'(slice(0, 13184, None), slice(None, None, None))' is an invalid key" Displayed in Logs
======================================================================================================

Symptom
-------

The following error message was displayed during training:

.. code-block::

   TypeError: '(slice(0, 13184, None), slice(None, None, None))' is an invalid key

Possible Causes
---------------

The possible causes are as follows:

The data selected for segmentation is incorrect.

Solution
--------

Run the following command to resolve the issue:

.. code-block::

   X = dataset.iloc[:,:-1].values

Summary and Suggestions
-----------------------

Before creating a training job, use the ModelArts development environment to debug the training code to maximally eliminate errors in code migration.
