:original_name: develop-modelarts-0001.html

.. _develop-modelarts-0001:

Introduction to Model Development
=================================

AI modeling involves two stages:

-  Development: To train using deep learning, you must set up and configure the environment and debug the code. For code debugging, it is recommended to use ModelArts development environments.
-  Experiment: To obtain an ideal model, you must optimize the datasets and hyperparameters through multiple rounds of experiments. ModelArts training is recommended.

In the two stages, code is designed, developed, and tested in repeated cycles. In the development stage, when the code becomes stable, the modeling process enters the experiment stage, during which hyperparameters are continuously optimized to iterate the model. In the experiment stage, when the training performance can be optimized, the modeling process returns to the development stage for optimizing code.

The following is part of the process for AI modeling.

|image1|

ModelArts provides model training, which allows you to review training results and tune model parameters based on the training results. You can select resource pools with different specifications for model training.

To train a model on ModelArts, follow these steps:

-  Use data management to label or preprocess imported training data, and upload the labeled data to OBS. For details, see :ref:`Preparing Data <develop-modelarts-0002>`.
-  Create an algorithm for model training. For details, see :ref:`Preparing Algorithms <develop-modelarts-0003>`.
-  Create a training job on the ModelArts console. For details, see :ref:`Creating a Training Job <develop-modelarts-0011>`.
-  Stop or delete a training job. For details, see :ref:`Stopping, Rebuilding, or Searching for a Training Job <develop-modelarts-0017>`.
-  Troubleshoot if you encounter any problem during training. For details, see "Training Jobs" in *Troubleshooting*.

.. |image1| image:: /_static/images/en-us_image_0000002374845549.png
