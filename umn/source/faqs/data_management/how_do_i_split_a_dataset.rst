:original_name: modelarts_05_3144.html

.. _modelarts_05_3144:

How Do I Split a Dataset?
=========================

When you publish a dataset, only the dataset of the image classification, object detection, text classification, or sound classification type supports data splitting.

By default, data splitting is disabled. After this function is enabled, set the training and validation ratios.

Enter a value ranging from 0 to 1 for the training set ratio. After the training set ratio is set, the validation set ratio is determined. The sum of the training set ratio and the validation set ratio is 1.

The training set ratio is the ratio of sample data used for model training. The validation set ratio is the ratio of the sample data used for model validation. The training and validation ratios affect the performance of training templates.
