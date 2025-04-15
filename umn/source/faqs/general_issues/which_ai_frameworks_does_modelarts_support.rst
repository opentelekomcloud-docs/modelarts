:original_name: modelarts_05_0128.html

.. _modelarts_05_0128:

Which AI Frameworks Does ModelArts Support?
===========================================

The AI frameworks and versions supported by ModelArts vary slightly based on the development environment notebook, training jobs, and model inference (Model management and deployment). The following describes the AI frameworks supported by each module.

Development Environment Notebook
--------------------------------

The image and versions supported by development environment notebook instances vary based on runtime environments.

.. table:: **Table 1** Images supported by notebook of the new version

   +------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+----------------+------------+-------------------+
   | Image                                                      | Description                                                                                                    | Supported Chip | Remote SSH | Online JupyterLab |
   +============================================================+================================================================================================================+================+============+===================+
   | mindspore1.7.0-cann5.1.0-py3.7-euler2.8.3                  | Ascend+ARM algorithm development and training. MindSpore is preset in the AI engine.                           | Ascend 910     | Yes        | Yes               |
   +------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+----------------+------------+-------------------+
   | mindstudio5.0.rc1-ascend910-cann5.1.rc1-euler2.8.3-aarch64 | Ascend+ARM algorithm development and training. MindSpore is preset in the AI engine.                           | Ascend 910     | Yes        | No                |
   +------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+----------------+------------+-------------------+
   | mindspore1.8.0-cann5.1.2-py3.7-euler2.8.3                  | Ascend+ARM algorithm development and training. MindSpore is preset in the AI engine.                           | Ascend 910     | Yes        | Yes               |
   +------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+----------------+------------+-------------------+
   | tensorflow1.15-cann5.1.0-py3.7-euler2.8.3                  | Ascend+ARM algorithm development and training. TensorFlow is preset in the AI engine.                          | Ascend 910     | Yes        | Yes               |
   +------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+----------------+------------+-------------------+
   | mindspore_2.0.0-cann_6.3.0-py_3.7-euler_2.8.3              | Ascend- and Arm-powered public image for algorithm development and training, with built-in AI engine MindSpore | Ascend 910     | Yes        | Yes               |
   +------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+----------------+------------+-------------------+
   | pytorch_1.11.0-cann_6.3.0-py_3.7-euler_2.8.3               | Ascend- and Arm-powered public image for algorithm development and training, with built-in AI engine PyTorch   | Ascend 910     | Yes        | Yes               |
   +------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+----------------+------------+-------------------+
   | tensorflow1.15-mindspore1.7.0-cann5.1.0-euler2.8-aarch64   | Ascend+ARM algorithm development and training. TensorFlow and MindSpore are preset in the AI engine.           | Ascend 910     | Yes        | Yes               |
   +------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+----------------+------------+-------------------+
   | tensorflow_1.15.0-cann_6.3.0-py_3.7-euler_2.8.3            | Ascend+ARM algorithm development and training. MindSpore is preset in the AI engine.                           | Ascend 910     | Yes        | Yes               |
   +------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+----------------+------------+-------------------+
   | tensorflow1.15.0-cann5.1.2-py3.7-euler2.8.3                | Ascend+ARM algorithm development and training. MindSpore is preset in the AI engine.                           | Ascend 910     | Yes        | Yes               |
   +------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+----------------+------------+-------------------+

.. table:: **Table 2** Images supported by notebook of the old version

   +-------------------------------------+--------------------------------+----------------+
   | Runtime Environment                 | Built-in AI Engine and Version | Supported Chip |
   +=====================================+================================+================+
   | Ascend-Powered-Engine 1.0 (Python3) | MindSpore 1.2.0                | Ascend 910     |
   +-------------------------------------+--------------------------------+----------------+
   |                                     | MindSpore 1.1.1                | Ascend 910     |
   +-------------------------------------+--------------------------------+----------------+
   |                                     | TensorFlow 1.15.0              | Ascend 910     |
   +-------------------------------------+--------------------------------+----------------+

Training Jobs
-------------

The built-in training engines in the new version are named in the following format:

.. code-block::

   <Training engine name_version>-[cpu | <cuda_version | cann_version >]-<py_version>-<OS name_version>-< x86_64 | aarch64>

.. table:: **Table 3** AI engines supported by training jobs of the new version

   +-----------------------+----------------+---------------------+----------------+---------------------------------------------------------+----------------------------------+
   | Runtime Environment   | Supported Chip | System Architecture | System Version | AI Engine and Version                                   | Supported CUDA or Ascend Version |
   +=======================+================+=====================+================+=========================================================+==================================+
   | Ascend-Powered-Engine | Ascend 910     | aarch64             | Euler 2.8      | mindspore_2.0.0-cann_6.3.0-py_3.7-euler_2.8.3-aarch64   | cann_6.3.0                       |
   +-----------------------+----------------+---------------------+----------------+---------------------------------------------------------+----------------------------------+
   | PyTorch               | Ascend 910     | aarch64             | Euler 2.8      | pytorch_1.11.0-cann_6.3.0-py_3.7-euler_2.8.3-aarch64    | cann_6.3.0                       |
   +-----------------------+----------------+---------------------+----------------+---------------------------------------------------------+----------------------------------+
   | TensorFlow            | Ascend 910     | aarch64             | Euler 2.8      | tensorflow_1.15.0-cann_6.3.0-py_3.7-euler_2.8.3-aarch64 | cann_6.3.0                       |
   +-----------------------+----------------+---------------------+----------------+---------------------------------------------------------+----------------------------------+

Supported AI Engines for ModelArts Inference
--------------------------------------------

If you import a model from a template or OBS to create a model, the following AI engines and versions are supported.

.. note::

   -  Runtime environments marked with **recommended** are unified runtime images, which will be used as mainstream base inference images.
   -  Images of the old version will be discontinued. Use unified images.
   -  The base images to be removed are no longer maintained.
   -  Naming a unified runtime image: <*AI engine name and version*> - <*Hardware and version*: CPU, CUDA, or CANN> - <*Python version*> - <*OS version*> - <*CPU architecture*>

.. table:: **Table 4** Supported AI engines and their runtime

   ========== =======================================================
   Engine     Runtime
   ========== =======================================================
   TensorFlow tensorflow_1.15.0-cann_6.3.0-py_3.7-euler_2.8.3-aarch64
   MindSpore  mindspore_2.0.0-cann_6.3.0-py_3.7-euler_2.8.3-aarch64
   PyTorch    pytorch_1.11.0-cann_6.3.0-py_3.7-euler_2.8.3-aarch64
   ========== =======================================================
