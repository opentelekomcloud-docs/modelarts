:original_name: modelarts_23_0297.html

.. _modelarts_23_0297:

Bayesian Optimization (SMAC)
============================

In Bayesian optimization, it is assumed that there exists a functional relationship between hyperparameters and the objective function. Based on the evaluation values of the searched hyperparameters, the mean and variance of the objective function values at other search points are estimated through Gaussian process regression. The mean and variance are then used to construct the acquisition function. The next search point is the maximum value of the acquisition function. Compared with grid search, Bayesian optimization uses the previous evaluation results to reduce the number of iterations and shorten the search time. The disadvantage is that it is difficult to find the global optimal solution.

.. table:: **Table 1** Bayesian optimization parameters

   +-------------+---------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Description                                                                                       | Example Value                                                                                                                          |
   +=============+===================================================================================================+========================================================================================================================================+
   | num_samples | Number of hyperparameter groups for search attempts                                               | The value is an integer ranging from 10 to 20. The larger the value, the longer the search time and the better the effect.             |
   +-------------+---------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | kind        | Acquisition function type                                                                         | This value is string type. The default value is **ucb** and other value options are **ei** and **poi**. Do not change the default one. |
   +-------------+---------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | kappa       | Adjustment parameter of acquisition function type **ucb**, which is the upper confidence boundary | The value is float type. Do not change the default value.                                                                              |
   +-------------+---------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | xi          | Adjustment parameter of acquisition function types **poi** and **ei**                             | The value is float type. Do not change the default value.                                                                              |
   +-------------+---------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------+
