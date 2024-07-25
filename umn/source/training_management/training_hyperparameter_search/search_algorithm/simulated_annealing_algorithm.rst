:original_name: modelarts_23_0304_0.html

.. _modelarts_23_0304_0:

.. _en-us_topic_0000001916502166:

Simulated Annealing Algorithm
=============================

The simulated annealing algorithm is a simple but effective variant on random search that leverages smoothness in the response surface. The annealing rate is not adaptive. The annealing algorithm is to choose one of the previous trial points as a starting point, and then to sample each hyperparameter from a similar distribution to the one specified in the prior, but whose density is more concentrated around the trial point we selected. The algorithm tends over time to sample from points closer and closer to the best ones. During the sampling, this algorithm may draw a runner-up trial as the best trail to avoid local optima at a certain probability.

.. table:: **Table 1** Parameters of the simulated annealing algorithm

   +--------------+----------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Description                                                                                              | Recommended Value                                                                                                              |
   +==============+==========================================================================================================+================================================================================================================================+
   | num_samples  | Number of hyperparameters to search                                                                      | The parameter is an integer ranging from 10 to 20. A larger value indicates a longer search time and better search efficiency. |
   +--------------+----------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | avg_best_idx | Mean of geometric distribution over which trial to explore around, selecting from trials sorted by score | This parameter is a float. You are not advised to change it.                                                                   |
   +--------------+----------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | shrink_coef  | Rate of reduction in the size of sampling neighborhood as more points have been explored                 | This parameter is a float. You are not advised to change it.                                                                   |
   +--------------+----------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
