:original_name: modelarts_23_0283.html

.. _modelarts_23_0283:

Introduction to Custom Script
=============================

If the subscribed algorithms cannot meet your requirements or you want to migrate local algorithms to ModelArts for training, use the ModelArts built-in training engines to create algorithms. This method is also called using a custom script.

This section describes how to use a custom script to create an algorithm.

-  For details about ModelArts built-in engines and models, see :ref:`Built-in Training Engines <modelarts_23_0283__en-us_topic_0000001133191212_section194662011154910>`.
-  To migrate local algorithms to ModelArts, perform code adaptation. For details, see :ref:`Developing a Custom Script <modelarts_23_0240_0>`.
-  For details about how to use a custom script to create an algorithm on the ModelArts console, see :ref:`Creating an Algorithm <modelarts_23_0233>`.

.. _modelarts_23_0283__en-us_topic_0000001133191212_section194662011154910:

Built-in Training Engines
-------------------------

The following table lists the training engines and their versions supported by ModelArts.

.. note::

   -  MoXing is a distributed training acceleration framework developed by the ModelArts team. It is built on the open-source deep learning engines TensorFlow, MXNet, PyTorch, and Keras. If you use MoXing to compile a training script, select the corresponding AI engine and version based on your selected API when you create a training job.

.. table:: **Table 1** AI engines supported by training jobs of the new version

   +---------------------------+----------------+---------------------+----------------+----------------------------------------------------------------------+----------------------------------+
   | Work Environment          | Supported Chip | System Architecture | System Version | AI Engine and Version                                                | Supported CUDA or Ascend Version |
   +===========================+================+=====================+================+======================================================================+==================================+
   | **TensorFlow**            | CPU or GPU     | x86_64              | Ubuntu 18.04   | tensorflow_2.1.0-cuda_10.1-py_3.7-ubuntu_18.04-x86_64                | CUDA 10.1                        |
   +---------------------------+----------------+---------------------+----------------+----------------------------------------------------------------------+----------------------------------+
   | **PyTorch**               | CPU or GPU     | x86_64              | Ubuntu 18.04   | pytorch_1.8.0-cuda_10.2-py_3.7-ubuntu_18.04-x86_64                   | CUDA 10.2                        |
   +---------------------------+----------------+---------------------+----------------+----------------------------------------------------------------------+----------------------------------+
   | **Ascend-Powered-Engine** | Ascend 910     | AArch64             | Euler 2.8      | mindspore_1.7.0-cann_5.1.0-py_3.7-euler_2.8.3-aarch64                | cann_5.1.0                       |
   +---------------------------+----------------+---------------------+----------------+----------------------------------------------------------------------+----------------------------------+
   |                           |                |                     |                | tensorflow_1.15-cann_5.0.4-py_3.7-euler_2.8.3-aarch64                | cann_5.0.4                       |
   +---------------------------+----------------+---------------------+----------------+----------------------------------------------------------------------+----------------------------------+
   | **MPI**                   | GPU            | x86_64              | Ubuntu 18.04   | mindspore_1.3.0-cuda_10.1-py_3.7-ubuntu_1804-x86_64                  | cuda_10.1                        |
   +---------------------------+----------------+---------------------+----------------+----------------------------------------------------------------------+----------------------------------+
   | **Horovod**               | GPU            | x86_64              | ubuntu_18.04   | horovod_0.20.0-tensorflow_2.1.0-cuda_10.1-py_3.7-ubuntu_18.04-x86_64 | cuda_10.1                        |
   +---------------------------+----------------+---------------------+----------------+----------------------------------------------------------------------+----------------------------------+
   |                           |                |                     |                | horovod_0.22.1-pytorch_1.8.0-cuda_10.2-py_3.7-ubuntu_18.04-x86_64    | cuda_10.2                        |
   +---------------------------+----------------+---------------------+----------------+----------------------------------------------------------------------+----------------------------------+
