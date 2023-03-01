:original_name: modelarts_04_0005.html

.. _modelarts_04_0005:

Environment Preparations
========================

ModelArts SDK can be used in the following environments:

-  ModelArts SDK has been integrated into ModelArts Notebook and can be directly used without session authentication.

   On the ModelArts management console, access the **DevEnviron** module, create a notebook instance, and directly call the ModelArts SDK APIs in the **Terminal** or Ipynb file. You can call the SDK in a notebook instance to perform operations such as OBS management, job management, model management, and service management by referring to the API reference.

-  ModelArts SDK can be installed and configured in the local Windows- or Linux-based environment.

   Download and install Python 2 or Python 3 from the `official website of Python <https://www.python.org/>`__ (Python 2.7, Python 3.6, Python 3.7, or later is recommended), and configure a Python runtime environment.

   .. note::

      -  After Python is installed, you can enter **python** or **python3** in the command line interface (CLI) and press **Enter** to view the Python version and enter the Python environment.
      -  In the Windows-based environment, if a message is displayed indicating that the command is not an internal or external command, add the Python and pip installation paths to **Path** in the environment variable. The pip installation path is usually the **Scripts** folder in the directory where Python is located.
