:original_name: modelarts_trouble_0058.html

.. _modelarts_trouble_0058:

Error Message "DataFrame.dtypes for data must be int, float or bool" Displayed in Logs
======================================================================================

Symptom
-------

The following error message was displayed during training:

.. code-block::

   DataFrame.dtypes for data must be int, float or bool

Possible Causes
---------------

The possible causes are as follows:

The training data is not of the int, float, or bool type.

Solution
--------

Run the following commands to convert the error column:

.. code-block::

   from sklearn import preprocessing
   lbl = preprocessing.LabelEncoder()
   train_x['acc_id1'] = lbl.fit_transform(train_x['acc_id1'].astype(str)

Summary and Suggestions
-----------------------

Before creating a training job, use the ModelArts development environment to debug the training code to maximally eliminate errors in code migration.
