:original_name: modelarts_21_0018.html

.. _modelarts_21_0018:

Training a Model
================

After the data is labeled, train a model for predictive analytics. You can publish the model as a real-time inference service.

Procedure
---------

#. On the **ExeML** page, click the name of the project that has been created. The **Label Data** tab page is displayed. Select the label column and its data type.

#. On the **Label Data** tab page, click **Train** in the lower left corner. In the displayed **Training Configuration** dialog box, select an instance flavor used for training, click **Next** to go to the configuration page, confirm the specifications, and click **Submit** to start model training.

   The training takes a certain period of time. If you close or exit the page, the system continues training until it is complete.

#. On the **Train Model** tab page, wait until the training status changes from **Running** to **Completed**.

#. View the training details, such as the label column, data type, accuracy, and evaluation result.

   The example is a discrete value of binary classification. For details about the evaluation result parameters, see :ref:`Table 1 <en-us_topic_0000002340732168__en-us_topic_0000001846056137_en-us_topic_0000001096914569_table1827411471920>`.

   For details about the evaluation results generated for different data types of label columns, see :ref:`Evaluation Results <en-us_topic_0000002340732168__en-us_topic_0000001846056137_en-us_topic_0000001096914569_section02494566510>`.

.. note::

   An ExeML project supports multiple rounds of training, and each round generates a version. For example, the first training version is **V001 (**\ *xxx*\ **)**, and the next version is **V002 (**\ *xxx*\ **)**. The trained models can be managed by training version. After the trained model meets your requirements, deploy the model as a service.

.. _en-us_topic_0000002340732168__en-us_topic_0000001846056137_en-us_topic_0000001096914569_section02494566510:

Evaluation Results
------------------

The parameters in evaluation results vary depending on the training data type.

-  Discrete values

   The evaluation parameters include recall, precision, accuracy, and F1 score, which are described in the following table.

   .. _en-us_topic_0000002340732168__en-us_topic_0000001846056137_en-us_topic_0000001096914569_table1827411471920:

   .. table:: **Table 1** Parameters in discrete value evaluation results

      +-----------+-------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter | Description                                                                                                                                     |
      +===========+=================================================================================================================================================+
      | Recall    | Fraction of correctly predicted samples over all samples predicted as a class. It shows the ability of a model to distinguish positive samples. |
      +-----------+-------------------------------------------------------------------------------------------------------------------------------------------------+
      | Precision | Fraction of correctly predicted samples over all samples predicted as a class. It shows the ability of a model to distinguish negative samples. |
      +-----------+-------------------------------------------------------------------------------------------------------------------------------------------------+
      | Accuracy  | Fraction of correctly predicted samples over all samples. It shows the general ability of a model to recognize samples.                         |
      +-----------+-------------------------------------------------------------------------------------------------------------------------------------------------+
      | F1 Score  | Harmonic average of the precision and recall of a model. It is used to evaluate the quality of a model. A high F1 score indicates a good model. |
      +-----------+-------------------------------------------------------------------------------------------------------------------------------------------------+

-  Continuous values

   The evaluation parameters include Mean Absolute Error (MAE), Mean Squared Error (MSE), and Root Mean Squared Error (RMSE). The three error values represent a difference between a real value and a predicted value. During multiple rounds of modeling, a group of error values is generated for each round of modeling. Use these error values to determine the quality of a model. A smaller error value indicates a better model.
