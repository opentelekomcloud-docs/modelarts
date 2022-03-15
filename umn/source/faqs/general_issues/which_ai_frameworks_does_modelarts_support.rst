Which AI Frameworks Does ModelArts Support?
===========================================

Supported AI frameworks and versions of ModelArts vary slightly based on the development environment, training jobs, and model inference (model management and deployment). The following describes the AI frameworks supported by each module.

Development Environment
-----------------------

Notebook instances in the development environment support different AI engines and versions based on specific work environments (that is, different Python versions). After creating a notebook instance in the corresponding work environment, create a file based on the corresponding version in `Table 1 <#modelarts050128enustopic0246510446table4362414101>`__. ModelArts notebook instances support multiple engines. That is, a notebook instance can use all supported engines. Different engines can be switched quickly and conveniently.



.. _modelarts050128enustopic0246510446table4362414101:

.. table:: **Table 1** AI engines

   +------------------------------------------+--------------------------------+----------------+
   | Work Environment                         | Built-in AI Engine and Version | Supported Chip |
   +==========================================+================================+================+
   | Multi-Engine 1.0 (Python 3, Recommended) | MXNet-1.2.1                    | GPU            |
   +------------------------------------------+--------------------------------+----------------+
   |                                          | PySpark-2.3.2                  | CPU            |
   +------------------------------------------+--------------------------------+----------------+
   |                                          | Pytorch-1.0.0                  | GPU            |
   +------------------------------------------+--------------------------------+----------------+
   |                                          | TensorFlow-1.13.1              | GPU            |
   +------------------------------------------+--------------------------------+----------------+
   |                                          | XGBoost-Sklearn                | CPU            |
   +------------------------------------------+--------------------------------+----------------+
   | Multi-Engine 2.0 (Python3)               | Pytorch-1.4.0                  | GPU            |
   +------------------------------------------+--------------------------------+----------------+
   |                                          | TensorFlow-2.1.0               | CPU/GPU        |
   +------------------------------------------+--------------------------------+----------------+
   | Ascend-Powered-Engine 1.0 (Python3)      | MindSpore-1.1.1                | Ascend 910     |
   +------------------------------------------+--------------------------------+----------------+
   |                                          | TensorFlow-1.15.0              | Ascend 910     |
   +------------------------------------------+--------------------------------+----------------+

Training Jobs
-------------

Supported AI engines and versions when creating training jobs are as follows:



.. _modelarts050128enustopic0246510446table97515527121:

.. table:: **Table 2** AI engines supported by training jobs

   +-----------------------+----------------+---------------------+----------------+-----------------------------------+----------------------------------+
   | Environment           | Supported Chip | System Architecture | System Version | AI Engine and Version             | Supported CUDA or Ascend Version |
   +=======================+================+=====================+================+===================================+==================================+
   | TensorFlow            | CPU and GPU    | x86_64              | Ubuntu 16.04   | TF-1.13.1-python3.6               | CUDA 10.0                        |
   +-----------------------+----------------+---------------------+----------------+-----------------------------------+----------------------------------+
   |                       |                |                     |                | TF-2.1.0-python3.6                | CUDA 10.1                        |
   +-----------------------+----------------+---------------------+----------------+-----------------------------------+----------------------------------+
   | Caffe                 | CPU and GPU    | x86_64              | Ubuntu 16.04   | Caffe-1.0.0-python2.7             | CUDA 8.0                         |
   +-----------------------+----------------+---------------------+----------------+-----------------------------------+----------------------------------+
   | Spark_MLlib           | CPU            | x86_64              | Ubuntu 16.04   | Spark-2.3.2-python3.6             | N/A                              |
   +-----------------------+----------------+---------------------+----------------+-----------------------------------+----------------------------------+
   | XGBoost-Sklearn       | CPU            | x86_64              | Ubuntu 16.04   | Scikit_Learn-0.18.1-python3.6     | N/A                              |
   +-----------------------+----------------+---------------------+----------------+-----------------------------------+----------------------------------+
   | PyTorch               | CPU and GPU    | x86_64              | Ubuntu 16.04   | PyTorch-1.3.0-python3.6           | CUDA 10.0                        |
   +-----------------------+----------------+---------------------+----------------+-----------------------------------+----------------------------------+
   |                       |                |                     |                | PyTorch-1.4.0-python3.6           | CUDA 10.1                        |
   +-----------------------+----------------+---------------------+----------------+-----------------------------------+----------------------------------+
   | Ascend-Powered-Engine | Ascend 910     | AArch64             | EulerOS 2.8    | Mindspore-1.1.1-python3.7-aarch64 | C76                              |
   +-----------------------+----------------+---------------------+----------------+-----------------------------------+----------------------------------+
   |                       |                |                     |                | TF-1.15-python3.7-aarch64         | C76                              |
   +-----------------------+----------------+---------------------+----------------+-----------------------------------+----------------------------------+
   | MindSpore-GPU         | CPU and GPU    | x86_64              | Ubuntu 18.04   | MindSpore-1.1.0-python3.7         | CUDA 10.1                        |
   +-----------------------+----------------+---------------------+----------------+-----------------------------------+----------------------------------+

Model Inference
---------------

For imported models and model inference is completed on ModelArts, supported engines and their runtime are as follows:



.. _modelarts050128enustopic0246510446table195551745191318:

.. table:: **Table 3** Supported AI engines and their runtime

   +-----------------------+-------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Engine                | Runtime                 | Precautions                                                                                                                                                                                                                                                                                |
   +=======================+=========================+============================================================================================================================================================================================================================================================================================+
   | TensorFlow            | python3.6               | -  TensorFlow 1.8.0 is used in **python2.7** and **python3.6**.                                                                                                                                                                                                                            |
   |                       |                         | -  **python3.6**, **python2.7**, and **tf2.1-python3.7** indicate that the model can run on both CPUs and GPUs. For other runtime values, if the suffix contains **cpu** or **gpu**, the model can run only on CPUs or GPUs.                                                               |
   |                       | python2.7               | -  The default runtime is **python2.7**.                                                                                                                                                                                                                                                   |
   |                       |                         |                                                                                                                                                                                                                                                                                            |
   |                       | tf1.13-python2.7-gpu    |                                                                                                                                                                                                                                                                                            |
   |                       |                         |                                                                                                                                                                                                                                                                                            |
   |                       | tf1.13-python2.7-cpu    |                                                                                                                                                                                                                                                                                            |
   |                       |                         |                                                                                                                                                                                                                                                                                            |
   |                       | tf1.13-python3.6-gpu    |                                                                                                                                                                                                                                                                                            |
   |                       |                         |                                                                                                                                                                                                                                                                                            |
   |                       | tf1.13-python3.6-cpu    |                                                                                                                                                                                                                                                                                            |
   |                       |                         |                                                                                                                                                                                                                                                                                            |
   |                       | tf1.13-python3.7-cpu    |                                                                                                                                                                                                                                                                                            |
   |                       |                         |                                                                                                                                                                                                                                                                                            |
   |                       | tf1.13-python3.7-gpu    |                                                                                                                                                                                                                                                                                            |
   |                       |                         |                                                                                                                                                                                                                                                                                            |
   |                       | tf2.1-python3.7         |                                                                                                                                                                                                                                                                                            |
   |                       |                         |                                                                                                                                                                                                                                                                                            |
   |                       | tf1.15-aarch64-c76-d910 |                                                                                                                                                                                                                                                                                            |
   +-----------------------+-------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | MXNet                 | python3.7               | -  MXNet 1.2.1 is used in **python3.6** and **python3.7**.                                                                                                                                                                                                                                 |
   |                       |                         | -  **python3.6** and **python3.7** indicate that the model can run on both CPUs and GPUs.                                                                                                                                                                                                  |
   |                       | python3.6               | -  The default runtime is **python3.6**.                                                                                                                                                                                                                                                   |
   +-----------------------+-------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Caffe                 | python3.6               | -  Caffe 1.0.0 is used in **python3.6**, **python3.7**, **python3.6-gpu**, **python3.7-gpu**, **python3.6-cpu**, and **python3.7-cpu**.                                                                                                                                                    |
   |                       |                         | -  **python 3.6** and **python3.7** can only be used to run models on CPUs. For other runtime values, if the suffix contains **cpu** or **gpu**, the model can run only on CPUs or GPUs. Use the runtime of **python3.6-gpu**, **python3.7-gpu**, **python3.6-cpu**, or **python3.7-cpu**. |
   |                       | python3.7               | -  The default runtime is **python3.6**.                                                                                                                                                                                                                                                   |
   |                       |                         |                                                                                                                                                                                                                                                                                            |
   |                       | python3.6-gpu           |                                                                                                                                                                                                                                                                                            |
   |                       |                         |                                                                                                                                                                                                                                                                                            |
   |                       | python3.7-gpu           |                                                                                                                                                                                                                                                                                            |
   |                       |                         |                                                                                                                                                                                                                                                                                            |
   |                       | python3.6-cpu           |                                                                                                                                                                                                                                                                                            |
   |                       |                         |                                                                                                                                                                                                                                                                                            |
   |                       | python3.7-cpu           |                                                                                                                                                                                                                                                                                            |
   +-----------------------+-------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Spark_MLlib           | python3.6               | -  Spark_MLlib 2.3.2 is used in **python3.6**.                                                                                                                                                                                                                                             |
   |                       |                         | -  **python 3.6** can only be used to run models on CPUs.                                                                                                                                                                                                                                  |
   +-----------------------+-------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Scikit_Learn          | python3.6               | -  Scikit_Learn 0.18.1 is used in **python3.6**.                                                                                                                                                                                                                                           |
   |                       |                         | -  **python 3.6** can only be used to run models on CPUs.                                                                                                                                                                                                                                  |
   +-----------------------+-------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | XGBoost               | python3.6               | -  XGBoost 0.80 is used in **python3.6**.                                                                                                                                                                                                                                                  |
   |                       |                         | -  **python 3.6** can only be used to run models on CPUs.                                                                                                                                                                                                                                  |
   +-----------------------+-------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | PyTorch               | python3.6               | -  PyTorch 1.0 is used in **python3.6** and **python3.7**.                                                                                                                                                                                                                                 |
   |                       |                         | -  **python3.6**, **python3.7**, and **pytorch1.4-python3.7** indicate that the model can run on both CPUs and GPUs.                                                                                                                                                                       |
   |                       | python3.7               | -  The default runtime is **python3.6**.                                                                                                                                                                                                                                                   |
   |                       |                         |                                                                                                                                                                                                                                                                                            |
   |                       | pytorch1.4-python3.7    |                                                                                                                                                                                                                                                                                            |
   +-----------------------+-------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | MindSpore             | ms1.1-python3.7-c76     | MindSpore 1.1.1 is used.                                                                                                                                                                                                                                                                   |
   +-----------------------+-------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

