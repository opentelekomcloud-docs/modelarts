:original_name: modelarts_trouble_0055.html

.. _modelarts_trouble_0055:

Error Message "Unexpected keyword argument passed to optimizer" Displayed in Logs
=================================================================================

Symptom
-------

After Keras was upgraded to 2.3.0 or later, the following error message was displayed:

.. code-block::

   TypeError: Unexpected keyword argument passed to optimizer: learning_rate

Possible Causes
---------------

The possible causes are as follows:

Certain parameters have been renamed in Keras. For details, see `Keras 2.3.0 <https://github.com/keras-team/keras/releases/tag/2.3.0>`__.


.. figure:: /_static/images/en-us_image_0000001846137453.png
   :alt: **Figure 1** API changes

   **Figure 1** API changes

Solution
--------

Rename **learning_rate** **lr**.

Summary and Suggestions
-----------------------

Before creating a training job, use the ModelArts development environment to debug the training code to maximally eliminate errors in code migration.
