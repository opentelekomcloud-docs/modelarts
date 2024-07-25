:original_name: modelarts_23_0290.html

.. _modelarts_23_0290:

Introduction to Hyperparameter Search
=====================================

The new version of ModelArts training jobs supports hyperparameter search, which can automatically search for optimal hyperparameters for your models.

During model training, many hyperparameters, such as **learning_rate** and **weight_decay**, need to be adjusted based on actual requirements. This may cost an experienced algorithm engineer a lot of time and effort on manual optimization. However, the hyperparameter search supported by ModelArts can automatically optimize hyperparameters without the help of algorithm engineers and has higher optimization speed and precision than manual optimization.

ModelArts supports the following hyperparameter search algorithms:

-  :ref:`Bayesian Optimization (SMAC) <en-us_topic_0000001916662106>`
-  :ref:`TPE Algorithm <en-us_topic_0000001947261241>`
-  :ref:`Simulated Annealing Algorithm <en-us_topic_0000001916502166>`
