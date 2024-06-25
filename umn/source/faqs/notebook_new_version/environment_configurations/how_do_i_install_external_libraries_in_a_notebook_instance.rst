:original_name: modelarts_05_0022.html

.. _modelarts_05_0022:

How Do I Install External Libraries in a Notebook Instance?
===========================================================

Multiple environments such as Jupyter and Python have been integrated into ModelArts notebook to support many frameworks, including TensorFlow, MindSpore, PyTorch, and Spark. You can use **pip install** to install external libraries in Jupyter Notebook or on the **Terminal** page.

Installing External Libraries in Jupyter Notebook
-------------------------------------------------

You can use JupyterLab to install Shapely in the **TensorFlow-1.8** environment.

#. Open a notebook instance and access the **Launcher** page.

#. In the **Notebook** area, click **TensorFlow-1.8** and create an IPYNB file.

#. In the new notebook instance, enter the following command in the code input bar:

   **!pip install Shapely**

Installing External Libraries on the **Terminal** Page
------------------------------------------------------

You can use **pip** to install external libraries in the **TensorFlow-1.8** environment on the **Terminal** page. For example, to install Shapely:

#. Open a notebook instance and access the **Launcher** page.

#. In the **Other** area, click **Terminal** and create a terminal file.

#. Enter the following commands in the code input box to obtain the kernel of the current environment and activate the Python environment on which the installation depends:

   **cat /home/ma-user/README**

   **source /home/ma-user/anaconda3/bin/activate TensorFlow-1.8**

   .. note::

      To install TensorFlow in another Python environment, replace **TensorFlow-1.8** in the command with the target engine.


   .. figure:: /_static/images/en-us_image_0000001910019046.png
      :alt: **Figure 1** Activating the environment

      **Figure 1** Activating the environment

#. Run the following command in the code input box to install Shapely:

   **pip install Shapely**
