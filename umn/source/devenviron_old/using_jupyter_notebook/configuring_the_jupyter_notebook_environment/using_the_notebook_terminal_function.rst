:original_name: modelarts_23_0117.html

.. _modelarts_23_0117:

Using the Notebook Terminal Function
====================================

For developers who are used to coding, the terminal function is very convenient and practical. This section describes how to enable the terminal function in a notebook instance and switch the engine environment in the terminal.

.. _en-us_topic_0000001915042040__en-us_topic_0000001799496556_en-us_topic_0190535990_section78015461056:

Enabling the Notebook Terminal Function
---------------------------------------

#. In the notebook instance list, click **Open** in the **Operation** column of the target notebook instance to go to the **Jupyter Notebook** page.
#. On the **Files** tab page of the Jupyter page, click **New** and select **Terminal**. The **Terminal** page is displayed.

Switching Engine Environments on the Terminal
---------------------------------------------

You can switch to another AI engine environment in the terminal environment of Jupyter.

#. Create and open a notebook instance or open an existing notebook instance in the notebook instance list.

#. On the **Files** tab page of the Jupyter page, click **New** and select **Terminal**. The **Terminal** page is displayed.

#. View **README** in the current directory to obtain your required information. For example, to switch to **TensorFlow-1.15.0**, run the **source /home/ma-user/anaconda3/bin/activate TensorFlow-1.15.0** command. To exist the environment, run the **source deactivate** command.


   .. figure:: /_static/images/en-us_image_0000001846057393.png
      :alt: **Figure 1** Output after command execution

      **Figure 1** Output after command execution
