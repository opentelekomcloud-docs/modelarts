.. _modelarts_23_0040:

Installing External Libraries and Kernels in Notebook Instances
===============================================================

Multiple environments have been installed in ModelArts notebook instances, including TensorFlow. You can use **pip install** to install external libraries from a Jupyter notebook or terminal to facilitate use.

Installing an External Library from a Jupyter Notebook
------------------------------------------------------

Assume that you want to install Shapely from a notebook instance. Follow the following instructions:

#. In the left navigation pane of the ModelArts management console, choose **DevEnviron > Notebooks**. Open a notebook instance in the displayed notebook instance list.

#. In the **Jupyter Notebook** page that is displayed, click **New** and select the required AI engine from the drop-down list.

#. In the displayed window, type the following command in the code input bar to install Shapely:

   **pip install shapely**

Installing an External Library from a Terminal
----------------------------------------------

Assume that you want to install Shapely from the terminal of a notebook instance by using pip. Follow the following instructions:

#. In the left navigation pane of the ModelArts management console, choose **DevEnviron > Notebooks**. Open a notebook instance in the displayed notebook instance list.

#. In the displayed Jupyter dashboard, click **New** and choose **Terminal** from the shortcut menu.

#. For a notebook instance that does not use the AI engine of the **Multi-Engine** type, enter the following command in the code input bar to install Shapely:

   **/opt/conda/envs/python27_tf/bin/pip install Shapely**

#. The **Multi-Engine** notebook instance can use multiple engines. By referring to the **README** file in the **/home/ma-user/** path, switch to the installation package of the corresponding engine environment and install Shapely. For example, you can install Shapely from TensorFlow-1.13.1 with the following code:

   .. code-block::

      source /home/ma-user/anaconda3/bin/activate TensorFlow-1.13.1
      pip install shapely

.. note::

   When you create a ModelArts training job, a new independent running environment is started, which is not associated with the packages installed in the Notebook environment. Therefore, add **os.system('pip install xxx')** to the startup code before importing the installation package.

   For example, if you need to use the Shapely dependency in the training job, add the following code to the startup code:

   .. code-block::

      os.system('pip install Shapely')
      import Shapely
