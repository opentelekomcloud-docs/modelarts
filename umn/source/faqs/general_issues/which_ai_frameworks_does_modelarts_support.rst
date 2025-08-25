:original_name: modelarts_05_0128.html

.. _modelarts_05_0128:

Which AI Frameworks Does ModelArts Support?
===========================================

The AI frameworks and versions supported by ModelArts vary slightly based on the development environment notebook, training jobs, and model inference (Model management and deployment). The following describes the AI frameworks supported by each module.

Development Environment Notebook
--------------------------------

The image and versions supported by development environment notebook instances vary based on runtime environments.

.. table:: **Table 1** Images supported by notebook of the new version

   ===== =========== ============== ========== =================
   Image Description Supported Chip Remote SSH Online JupyterLab
   ===== =========== ============== ========== =================
   ===== =========== ============== ========== =================

Training Jobs
-------------

The built-in training engines in the new version are named in the following format:

.. code-block::

   <Training engine name_version>-[cpu | <cuda_version | cann_version >]-<py_version>-<OS name_version>-< x86_64 | aarch64>

.. table:: **Table 2** AI engines supported by training jobs of the new version

   +---------------------+----------------+---------------------+----------------+-----------------------+----------------+
   | Runtime Environment | Supported Chip | System Architecture | System Version | AI Engine and Version | Supported CUDA |
   +=====================+================+=====================+================+=======================+================+
   +---------------------+----------------+---------------------+----------------+-----------------------+----------------+

Supported AI Engines for ModelArts Inference
--------------------------------------------

If you import a model from a template or OBS to create a model, the following AI engines and versions are supported.

.. note::

   -  Runtime environments marked with **recommended** are unified runtime images, which will be used as mainstream base inference images.
   -  Images of the old version will be discontinued. Use unified images.
   -  The base images to be removed are no longer maintained.
   -  Naming a unified runtime image: <*AI engine name and version*> - <*Hardware and version*: CPU, CUDA, or CANN> - <*Python version*> - <*OS version*> - <*CPU architecture*>

.. table:: **Table 3** Supported AI engines and their runtime

   ========== =======================================================
   Engine     Runtime
   ========== =======================================================
   TensorFlow tensorflow_1.15.0-cann_6.3.0-py_3.7-euler_2.8.3-aarch64
   MindSpore  mindspore_2.0.0-cann_6.3.0-py_3.7-euler_2.8.3-aarch64
   PyTorch    pytorch_1.11.0-cann_6.3.0-py_3.7-euler_2.8.3-aarch64
   ========== =======================================================
