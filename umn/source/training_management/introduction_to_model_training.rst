Introduction to Model Training
==============================

ModelArts provides model training for you to view the training effect, based on which you can adjust your model parameters. You can select resource pools (CPU or GPU) with different instance flavors for model training. In addition to the models developed by users, ModelArts also provides built-in algorithms. You can directly adjust parameters of the built-in algorithms, instead of developing a model by yourself, to obtain a satisfactory model.

Description of the Model Training Function
------------------------------------------



.. _modelarts_23_0044__en-us_topic_0129633060_table138422031155511:

.. table:: **Table 1** Function description

   +---------------------------------------+---------------------------------------+---------------------------------------+
   | Function                              | Description                           | Reference                             |
   +=======================================+=======================================+=======================================+
   | Training job management               | You can create training jobs, manage  | `Creating a Training                  |
   |                                       | training job versions, and view       | Job <modelarts_23_0235.html>`__       |
   |                                       | details of training jobs, and         |                                       |
   |                                       | evaluation details.                   | `Managing Training Job                |
   |                                       |                                       | Versions <modelarts_23_0047.html>`__  |
   |                                       |                                       |                                       |
   |                                       |                                       | `Viewing Job                          |
   |                                       |                                       | Details <modelarts_23_0048.html>`__   |
   +---------------------------------------+---------------------------------------+---------------------------------------+
   | Job parameter management              | You can save the parameter settings   | `Managing Job                         |
   |                                       | of a training job (including the data | P                                     |
   |                                       | source, algorithm source, running     | arameters <modelarts_23_0049.html>`__ |
   |                                       | parameters, resource pool parameters, |                                       |
   |                                       | and more) as a job parameter, which   |                                       |
   |                                       | can be directly used when you create  |                                       |
   |                                       | a training job, eliminating the need  |                                       |
   |                                       | to set parameters one by one. As      |                                       |
   |                                       | such, the configuration efficiency    |                                       |
   |                                       | can be greatly improved.              |                                       |
   +---------------------------------------+---------------------------------------+---------------------------------------+
   | Model training visualization          | TensorBoard and MindInsight           | `Managing Visualization               |
   |                                       | effectively display the computational | Jobs <modelarts_23_0050.html>`__      |
   |                                       | graph of a model in the running       |                                       |
   |                                       | process, the trend of all metrics in  |                                       |
   |                                       | time, and the data used in the        |                                       |
   |                                       | training.                             |                                       |
   +---------------------------------------+---------------------------------------+---------------------------------------+

