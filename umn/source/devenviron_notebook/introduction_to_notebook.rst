:original_name: modelarts_23_0033.html

.. _modelarts_23_0033:

Introduction to Notebook
========================

ModelArts integrates the open-source Jupyter Notebook and JupyterLab to provide you with online interactive development and debugging environments. You can use the Notebook on the ModelArts management console to compile and debug code and train models based on the code, without concerning installation and configurations.

.. _modelarts_23_0033__en-us_topic_0162690357_section191109611479:

Supported AI Engines
--------------------

Each development environment supports multiple AI engines that run independently. All supported AI engines can be used in the same notebook instance, and these engines can be switched quickly and conveniently.

.. note::

   -  Each ModelArts notebook instance can use all supported engines.

.. table:: **Table 1** AI engines

   +------------------------------------------+--------------------------------+----------------+
   | Work Environment                         | Built-in AI Engine and Version | Supported Chip |
   +==========================================+================================+================+
   | Multi-Engine 1.0 (Python 3, Recommended) | MXNet-1.2.1                    | CPU/GPU        |
   +------------------------------------------+--------------------------------+----------------+
   |                                          | PySpark-2.3.2                  | CPU            |
   +------------------------------------------+--------------------------------+----------------+
   |                                          | Pytorch-1.0.0                  | GPU            |
   +------------------------------------------+--------------------------------+----------------+
   |                                          | TensorFlow-1.13.1              | CPU/GPU        |
   +------------------------------------------+--------------------------------+----------------+
   |                                          | TensorFlow-1.8                 | CPU/GPU        |
   +------------------------------------------+--------------------------------+----------------+
   |                                          | XGBoost-Sklearn                | CPU            |
   +------------------------------------------+--------------------------------+----------------+
   | Multi-Engine 1.0 (Python2)               | Caffe-1.0.0                    | CPU/GPU        |
   +------------------------------------------+--------------------------------+----------------+
   |                                          | MXNet-1.2.1                    | CPU/GPU        |
   +------------------------------------------+--------------------------------+----------------+
   |                                          | PySpark-2.3.2                  | CPU            |
   +------------------------------------------+--------------------------------+----------------+
   |                                          | PyTorch1.0.0                   | GPU            |
   +------------------------------------------+--------------------------------+----------------+
   |                                          | TensorFlow-1.13.1              | CPU/GPU        |
   +------------------------------------------+--------------------------------+----------------+
   |                                          | TensorFlow-1.8                 | CPU/GPU        |
   +------------------------------------------+--------------------------------+----------------+
   |                                          | XGBoost-Sklearn                | CPU            |
   +------------------------------------------+--------------------------------+----------------+

Constraints
-----------

-  For security purposes, the root permission is not granted to the notebook instances integrated in ModelArts. You can use the non-privileged user **jovyan** or **ma-user** (using **Multi-Engine**) to perform operations. Therefore, you cannot use **apt-get** to install the OS software.
-  Notebook instances support only standalone training under the current AI engine framework. If you need to use distributed training, use ModelArts training jobs and specify multiple nodes in the resource pool.
-  ModelArts DevEnviron does not support apt-get. You can use a :ref:`custom image <modelarts_23_0084>` to train a model.
-  Notebook instances do not support GUI-related libraries, such as PyQt.
-  Notebook instances cannot be connected to DWS and database services.
-  Notebook instances cannot directly read files in OBS. You need to download the files to the local host. To access data in OBS, use or for interaction.
-  DevEnviron does not support TensorBoard. Use the visualization job function under **Training Jobs**.
-  After a notebook instance is created, you cannot modify its specifications. For example, you cannot change the CPU specifications to GPU specifications or change the work environment. Therefore, select the specifications required by the service when creating a notebook instance, or save your code and data to OBS in a timely manner during development so that you can quickly upload the code and data to a new notebook instance.
-  If the code output is still displayed after you close the page and open it again, use Terminal.
