:original_name: modelarts_21_0017.html

.. _modelarts_21_0017:

Selecting a Label Column
========================

After creating a predictive analytics project, select a label column and its data type. On the **Label Data** tab page, you can preview data and select the label column and its data type. Due to the limitation of the feature filtering algorithm, the label column must be the last column of the dataset. During model training, all data is used to train an inference model. The model uses the data of other columns as the input and outputs the inference value in the label column.

Procedure
---------

#. Select a label column. On the **Label Data** tab page, preview the data and select the training objective. Select the label column from the drop-down list of **Label Column**.

   The label column is the output of an inference model. In this project, the training objective is to identify iris species. The inference data will be output as discrete values in column **attr_5**. After the training objective is specified, click **Train**.

#. Select the data type of the label column. On the **Label Data** tab page, select a data type for **Label Column Data Type**.

   -  If the label column contains enumeration data, select **Discrete value**. The predictive analytics project will train a classification model.
   -  If the label column contains continuous numeric data, select **Continuous value**. The predictive analytics project will train a regression model.

   .. note::

      -  For discrete values, the evaluation result shows the recall, precision, accuracy, and F1 score after the model training is complete.
      -  For continuous values, the evaluation result shows mean absolute error (MAE), mean squared error (MSE), and root mean squared error (RMSE) after model training is complete.
