:original_name: modelarts_21_0069.html

.. _modelarts_21_0069:

Should I Access the Python Environment Same as the Notebook Kernel of the Current Instance in the Terminal?
===========================================================================================================

The following uses the TensorFlow-1.8 engine as an example. The operations on other engines are similar. You only need to replace the engine name and version number in the commands.

#. Open a notebook instance.
#. On the displayed Jupyter dashboard, click **New** and select **Terminal** from the shortcut menu.
#. The **README** file exists in the user directory on the **Terminal**. The file describes how to switch different Python environments.

   -  Enter the following command in the code input bar to search for a virtual environment name:

      **cat /home/ma-user/README**

   -  Enter the following command in the code input bar to activate different environments: For example, for the TensorFlow-1.8 engine in the Python2 environment, you can replace **\*\*** with **TensorFlow-1.8** in the command line. You can replace it with the engine of another version. Example:

      **source /home/ma-user/anaconda2/bin/activate \*\***
