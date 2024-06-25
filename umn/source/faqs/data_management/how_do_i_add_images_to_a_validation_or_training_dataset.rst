:original_name: modelarts_05_0506.html

.. _modelarts_05_0506:

How Do I Add Images to a Validation or Training Dataset?
========================================================

You are not allowed to manually add images to a training or validation dataset, but can only set a training and validation ratio. Then, the system randomly allocates the images to the training and validation datasets based on the ratio.

Setting a Training and Validation Ratio
---------------------------------------

When you publish a dataset, only the dataset of the image classification, object detection, text classification, or sound classification type supports data splitting.

By default, data splitting is disabled. After this function is enabled, set a training and validation ratio.

Enter a value ranging from 0 to 1 for the training set ratio. After the training set ratio is set, the validation set ratio is determined. The sum of the training set ratio and the validation set ratio is 1.

The training set ratio is the ratio of sample data used for model training. The validation set ratio is the ratio of the sample data used for model validation. The training and validation ratios affect the performance of training templates.
