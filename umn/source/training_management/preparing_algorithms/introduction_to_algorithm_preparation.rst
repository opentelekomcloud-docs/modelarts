:original_name: develop-modelarts-0004.html

.. _develop-modelarts-0004:

Introduction to Algorithm Preparation
=====================================

Machine learning explores general rules from limited volume of data and uses these rules to predict unknown data. To obtain more accurate prediction results, select a proper algorithm to train your model. ModelArts provides a large number of algorithm samples for different scenarios. This section describes algorithm sources and learning modes.

Algorithm Sources
-----------------

You can use one of the following methods to build a ModelArts model:

-  Using a preset image

   To use a custom algorithm, use a framework built in ModelArts. ModelArts supports most mainstream AI engines. For details, see :ref:`Built-in Training Engines <develop-modelarts-0007>`. These built-in engines pre-load some extra Python packages, such as NumPy. You can also use the **requirements.txt** file in the code directory to install dependency packages. For details about how to create a training job using a preset image, see :ref:`Using a Preset Image (Custom Script) <develop-modelarts-0006>`.

-  Using a custom image (For details about the new version of training, see :ref:`Using a Custom Image to Train a Model <docker-modelarts_0017>`.)

   The subscribed algorithms and built-in frameworks can be used in most training scenarios. In certain scenarios, ModelArts allows you to create custom images to train models. Custom images can be used to train models in ModelArts only after they are uploaded to the Software Repository for Container (SWR). Customizing an image requires a deep understanding of containers. Use this method only if the subscribed algorithms and custom scripts cannot meet your requirements.

Algorithm Learning Modes
------------------------

ModelArts allows you to train models in different modes as required.

-  Offline learning

   Offline learning is the most fundamental mode for model training. In this mode, all data required for training must be provided at a time, and optimizing the objective function stops when the training is complete. The advantage of this mode is that the trained models are stable, facilitating model verification and evaluation. However, it is time-consuming and low in storage space utilization.

-  Incremental learning

   Incremental learning is a continuous learning process. Compared with offline learning, it does not need to store all training data at a time, which alleviates the problem of limited storage resources. In addition, it saves a large amount of compute power and time, and reduces economic costs in retraining.
