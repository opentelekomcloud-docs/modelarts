:original_name: modelarts_23_0303_0.html

.. _modelarts_23_0303_0:

.. _en-us_topic_0000001947261241:

TPE Algorithm
=============

The tree-structured parzen estimator (TPE) algorithm uses the Gaussian mixture model to learn the model hyperparameters. On each trial, for each parameter, TPE fits one Gaussian mixture model l(x) to the set of parameter values associated with the best objective values, and another Gaussian mixture model g(x) to the remaining parameter values. It chooses the hyperparameter value that maximizes the ratio l(x)/g(x).

.. table:: **Table 1** TPE algorithm parameters

   +------------------+----------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
   | Parameter        | Description                                                                                                          | Recommended Value                                                                                                          |
   +==================+======================================================================================================================+============================================================================================================================+
   | num_samples      | Number of hyperparameter groups for search attempts                                                                  | The value is an integer ranging from 10 to 20. The larger the value, the longer the search time and the better the effect. |
   +------------------+----------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
   | n_initial_points | Number of random evaluations of the objective function before starting to approximate it with tree parzen estimators | The parameter is an integer. You are not advised to change it.                                                             |
   +------------------+----------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
   | gamma            | Quantile of the TPE algorithm to divide l(x) and g(x)                                                                | This parameter is a float ranging from 0 to 1. You are not advised to change it.                                           |
   +------------------+----------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
