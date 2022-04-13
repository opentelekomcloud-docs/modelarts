.. _modelarts_23_0326:

Introduction to Jupyter Notebook
================================

Jupyter Notebook is a web-based application for interactive computing. It can be applied to full-process computing: development, documentation, running code, and presenting results.

ModelArts integrates the open-source Jupyter Notebook. After creating a notebook instance, you can open the instance for development without the need for installation and configuration.

Notebook Kernel
---------------

-  A notebook kernel is an independent code execution environment. ModelArts Notebook supports multiple kernel types, such as TensorFlow 1.13.1 and PyTorch 1.0. A code execution environment contains the pre-installed and commissioned AI engines and dependencies.
-  When a kernel is selected to open a notebook instance, an IPython process is started at the backend of the notebook instance as the running environment to execute the code and command input on the page.
-  Each kernel type contains an independent Conda running environment to ensure that the AI engines are independent of each other. For example, if the Keras library is updated in a kernel of the TensorFlow type, the kernel of the MindSpore type will not be affected.

Differences Between Notebook Kernels and Common Interactive Python Interpreters
-------------------------------------------------------------------------------

A notebook kernel is an IPython running environment, which can be considered as an enhanced Python shell. Compared with a Python interpreter, a notebook kernel can execute shell scripts and integrate more visualized tools and magic commands. For details, see `IPython Documentation <https://ipython.readthedocs.io/>`__.
