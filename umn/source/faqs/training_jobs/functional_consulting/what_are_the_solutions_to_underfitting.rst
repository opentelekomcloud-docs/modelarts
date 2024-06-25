:original_name: modelarts_05_0170.html

.. _modelarts_05_0170:

What Are the Solutions to Underfitting?
=======================================

#. Increasing model complexity

   -  For an algorithm, add more high-order items to the regression model, improve the depth of the decision tree, or increase the number of hidden layers and hidden units of the neural network to increase model complexity.
   -  Discard the original algorithm and use a more complex algorithm or model. For example, use the neural network to replace the linear regression, and use the random forest to replace the decision tree.

#. Adding more features to make input data more expressive

   -  Feature mining is very important. Specifically, features with strong expression capabilities can outperform a large number of features with weak expression capabilities.
   -  Feature quality is the focus.

   -  To explore features with strong expression capabilities, you must have an in-depth understanding of data and application scenarios, which depends on experience.

#. Adjusting parameters and hyperparameters

   -  Neural network: learning rate, learning attenuation rate, number of hidden layers, number of units in a hidden layer, β1 and β2 parameters in the Adam optimization algorithm, and batch_size

   -  Other algorithms: number of trees in the random forest, number of clusters in *k*-means, and regularization parameter λ

#. Adding training data (not recommended)

   Underfitting is usually caused by weak model learning capabilities. Adding data cannot significantly increase the training effect.

#. Reducing regularization constraints

   Regularization aims to prevent model overfitting. If a model is underfitting instead of overfitting, reduce the regularization parameter **λ** or directly remove the regularization item.
