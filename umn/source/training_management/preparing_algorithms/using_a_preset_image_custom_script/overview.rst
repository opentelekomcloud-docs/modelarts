:original_name: develop-modelarts-0007.html

.. _develop-modelarts-0007:

Overview
========

If the subscribed algorithms cannot meet your requirements or you want to migrate local algorithms to ModelArts for training, use the ModelArts preset images to create algorithms. This method is also called using a preset image.

This section describes how to use a preset image to create an algorithm.

-  For details about ModelArts built-in engines and models, see :ref:`Built-in Training Engines <en-us_topic_0000002043018904__en-us_topic_0000001133191212_section194662011154910>`.
-  To migrate local algorithms to ModelArts, perform code adaptation. For details, see :ref:`Developing a Custom Script <develop-modelarts-0008>`.
-  For details about how to use a preset image to create an algorithm on the ModelArts console, see :ref:`Creating an Algorithm <develop-modelarts-0009>`.

.. _en-us_topic_0000002043018904__en-us_topic_0000001133191212_section194662011154910:

Built-in Training Engines
-------------------------

The following table lists the training engines and their versions supported by ModelArts.

.. table:: **Table 1** AI engines supported by training jobs of the new version

   +---------------------------+----------------+---------------------+----------------+---------------------------------------------------------+----------------------------------+
   | Runtime Environment       | Supported Chip | System Architecture | System Version | AI Engine and Version                                   | Supported CUDA or Ascend Version |
   +===========================+================+=====================+================+=========================================================+==================================+
   | **Ascend-Powered-Engine** | Ascend910      | aarch64             | Euler2.8       | mindspore_2.0.0-cann_6.3.0-py_3.7-euler_2.8.3-aarch64   | cann_6.3.0                       |
   +---------------------------+----------------+---------------------+----------------+---------------------------------------------------------+----------------------------------+
   | **PyTorch**               | Ascend910      | aarch64             | Euler2.8       | pytorch_1.11.0-cann_6.3.0-py_3.7-euler_2.8.3-aarch64    | cann_6.3.0                       |
   +---------------------------+----------------+---------------------+----------------+---------------------------------------------------------+----------------------------------+
   | **TensorFlow**            | Ascend910      | aarch64             | Euler2.8       | tensorflow_1.15.0-cann_6.3.0-py_3.7-euler_2.8.3-aarch64 | cann_6.3.0                       |
   +---------------------------+----------------+---------------------+----------------+---------------------------------------------------------+----------------------------------+
