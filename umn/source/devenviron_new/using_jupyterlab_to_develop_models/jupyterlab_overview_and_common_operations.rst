:original_name: modelarts_30_0009.html

.. _modelarts_30_0009:

JupyterLab Overview and Common Operations
=========================================

JupyterLab is the next-generation web-based interactive development environment of Jupyter Notebook, enabling you to compile notebooks, operate terminals, edit Markdown text, enable interaction, and view CSV files and images.

JupyterLab is the future mainstream development environment for developers. It has the same components as Jupyter Notebook, but offering more flexibility and powerful functions.

Accessing JupyterLab
--------------------

To access JupyterLab from a running notebook instance, perform the following operations:

#. Log in to the ModelArts management console. Choose **DevEnviron** > **Notebook** in the navigation pane on the left. The notebook list of the new version is displayed.

#. Click **Open** in the **Operation** column of a running notebook instance to access JupyterLab.


   .. figure:: /_static/images/en-us_image_0000001852878165.png
      :alt: **Figure 1** Accessing a notebook instance

      **Figure 1** Accessing a notebook instance

#. The **Launcher** page is automatically displayed. Perform required operations. For details, see `JupyterLab Documentation <https://jupyterlab.readthedocs.io/en/stable/>`__.


   .. figure:: /_static/images/en-us_image_0000001806319384.png
      :alt: **Figure 2** JupyterLab homepage

      **Figure 2** JupyterLab homepage

   -  **Notebook**: Select a kernel for running notebook, for example, TensorFlow or Python.
   -  **Console**: Call the terminal for command control.
   -  **Other**: Edit other files.

Creating an IPYNB File in JupyterLab
------------------------------------

On the JupyterLab homepage, click a proper AI engine in the **Notebook** area to create an IPYNB file.

The AI engines supported by each notebook instance vary depending on the runtime environment. The following figure is only an example. Select an AI engine based on site requirements.


.. figure:: /_static/images/en-us_image_0000001806159588.png
   :alt: **Figure 3** Selecting an AI engine and creating IPYNB file

   **Figure 3** Selecting an AI engine and creating IPYNB file

The created IPYNB file is displayed in the navigation pane on the left.


.. figure:: /_static/images/en-us_image_0000001853038381.png
   :alt: **Figure 4** Created IPYNB file

   **Figure 4** Created IPYNB file

Creating a Notebook File and Accessing the Console
--------------------------------------------------

A console is a Python terminal, which is similar to the native IDE of Python, displaying the output after a statement is entered.

On the JupyterLab homepage, click a proper AI engine in the **Console** area to create a notebook file.

The AI engines supported by each notebook instance vary depending on the runtime environment. The following figure is only an example. Select an AI engine based on site requirements.


.. figure:: /_static/images/en-us_image_0000001853038397.png
   :alt: **Figure 5** Selecting an AI engine and creating a console

   **Figure 5** Selecting an AI engine and creating a console

After the file is created, the console page is displayed.


.. figure:: /_static/images/en-us_image_0000001852879025.png
   :alt: **Figure 6** Creating a notebook file (console)

   **Figure 6** Creating a notebook file (console)

Editing a File in JupyterLab
----------------------------

JupyterLab allows you to open multiple notebook instances or files (such as HTML, TXT, and Markdown files) in one window and displays them on different tab pages.

In JupyterLab, you can customize the display of multiple files. In the file display area on the right, you can drag a file to adjust its position. Multiple files can be concurrently displayed.


.. figure:: /_static/images/en-us_image_0000001846057337.png
   :alt: **Figure 7** Customized display of multiple files

   **Figure 7** Customized display of multiple files

When writing code in a notebook instance, you can create multiple views of a file to synchronously edit the file and view execution results in real time.

To open multiple views, open an IPYNB file and choose **File** > **New View for Notebook**.


.. figure:: /_static/images/en-us_image_0000001846137269.png
   :alt: **Figure 8** Multiple views of a file

   **Figure 8** Multiple views of a file

Before coding in the code area of an IPYNB file in JupyterLab, add an exclamation mark (!) before the code.

For example, install an external library Shapely.

.. code-block::

   !pip install Shapely

For example, obtain PythonPath.

.. code-block::

   !echo $PYTHONPATH


.. figure:: /_static/images/en-us_image_0000001799498116.png
   :alt: **Figure 9** Running code

   **Figure 9** Running code

Renewing or Automatically Stopping a Notebook Instance
------------------------------------------------------

If you enable auto stop when you created or started a notebook instance, the remaining duration for stopping the instance is displayed in the upper right corner of JupyterLab. You can click the time for renewal.


.. figure:: /_static/images/en-us_image_0000001846057177.png
   :alt: **Figure 10** Remaining duration

   **Figure 10** Remaining duration


.. figure:: /_static/images/en-us_image_0000001846137417.png
   :alt: **Figure 11** Renewing an instance

   **Figure 11** Renewing an instance

Setting a Font
--------------

After accessing a ModelArts notebook instance from iOS, set the font to prevent abnormal display.


.. figure:: /_static/images/en-us_image_0000001846137333.png
   :alt: **Figure 12** Advanced Settings Editor

   **Figure 12** Advanced Settings Editor


.. figure:: /_static/images/en-us_image_0000001846057317.png
   :alt: **Figure 13** Set **fontFamily** to **Menlo**.

   **Figure 13** Set **fontFamily** to **Menlo**.

Common JupyterLab Buttons and Plug-ins
--------------------------------------


.. figure:: /_static/images/en-us_image_0000001846057181.png
   :alt: **Figure 14** Common JupyterLab buttons and plug-ins

   **Figure 14** Common JupyterLab buttons and plug-ins

.. table:: **Table 1** JupyterLab buttons

   +-----------+-----------------------------------------------------------------------------------------------------------+
   | Button    | Description                                                                                               |
   +===========+===========================================================================================================+
   | |image6|  | Open the **Launcher** page, on which you can quickly create notebook instances, consoles, or other files. |
   +-----------+-----------------------------------------------------------------------------------------------------------+
   | |image7|  | Create a folder.                                                                                          |
   +-----------+-----------------------------------------------------------------------------------------------------------+
   | |image8|  | Upload files.                                                                                             |
   +-----------+-----------------------------------------------------------------------------------------------------------+
   | |image9|  | Refresh the file directory.                                                                               |
   +-----------+-----------------------------------------------------------------------------------------------------------+
   | |image10| | Git plug-in, which can be used to access the GitHub code library associated with the notebook instance.   |
   +-----------+-----------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** JupyterLab plug-ins

   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | Plug-in                           | Description                                                                                                                           |
   +===================================+=======================================================================================================================================+
   | |image11|                         | List files. Click this button to show all files in the notebook instance.                                                             |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | |image12|                         | List ModelArts examples.                                                                                                              |
   |                                   |                                                                                                                                       |
   |                                   | ModelArts examples vary based on regions. For details about the ModelArts examples available in a region, see the management console. |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | |image13|                         | Display the terminals and kernels that are running in the current instance.                                                           |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | |image14|                         | Git plug-in, which can be used to quickly access the GitHub code library.                                                             |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | |image15|                         | Quickly show commands.                                                                                                                |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | |image16|                         | Property inspector.                                                                                                                   |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | |image17|                         | Display the tab pages for the opened files.                                                                                           |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | |image18|                         | Show the document organization.                                                                                                       |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+


.. figure:: /_static/images/en-us_image_0000001846137289.png
   :alt: **Figure 15** Buttons in the navigation bar

   **Figure 15** Buttons in the navigation bar

.. table:: **Table 3** Buttons in the navigation bar

   +----------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Button   | Description                                                                                                                          |
   +==========+======================================================================================================================================+
   | File     | Actions related to files and directories, such as creating, closing, saving, reloading, renaming, exporting, and printing notebooks. |
   +----------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Edit     | Actions related to editing documents and other activities in the IPYNB file, such as undoing, redoing, or cutting cells.             |
   +----------+--------------------------------------------------------------------------------------------------------------------------------------+
   | View     | Actions that alter the appearance of JupyterLab, such as showing the bar or expanding code.                                          |
   +----------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Run      | Actions for running code in different activities such as notebooks and code consoles.                                                |
   +----------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Kernel   | Actions for managing kernels, such as interrupting, restarting, or shutting down a kernel.                                           |
   +----------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Git      | Actions on the Git plug-in, which can be used to quickly access the GitHub code library.                                             |
   +----------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Tabs     | A list of the open documents and activities in the dock panel.                                                                       |
   +----------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Settings | Common settings and an advanced settings editor.                                                                                     |
   +----------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Help     | A list of JupyterLab and kernel help links.                                                                                          |
   +----------+--------------------------------------------------------------------------------------------------------------------------------------+


.. figure:: /_static/images/en-us_image_0000001799338424.png
   :alt: **Figure 16** Buttons in the menu bar of an IPYNB file

   **Figure 16** Buttons in the menu bar of an IPYNB file

.. table:: **Table 4** Buttons in the menu bar of an IPYNB file

   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | Button                            | Description                                                                                                                              |
   +===================================+==========================================================================================================================================+
   | |image19|                         | Save a file.                                                                                                                             |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | |image20|                         | Add a new cell.                                                                                                                          |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | |image21|                         | Cut the selected cell.                                                                                                                   |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | |image22|                         | Copy the selected cell.                                                                                                                  |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | |image23|                         | Paste the selected cell.                                                                                                                 |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | |image24|                         | Execute the selected cell.                                                                                                               |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | |image25|                         | Terminate a kernel.                                                                                                                      |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | |image26|                         | Restart a kernel.                                                                                                                        |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | |image27|                         | There are four options in the drop-down list:                                                                                            |
   |                                   |                                                                                                                                          |
   |                                   | **Code** (Python code), **Markdown** (Markdown code, typically used for comments), **Raw** (a conversion tool), and **-** (not modified) |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | |image28|                         | View historical code versions.                                                                                                           |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | |image29|                         | Git plug-in. The gray button indicates that the plug-in is unavailable in the current region.                                            |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | |image30|                         | Instance flavor.                                                                                                                         |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | |image31|                         | Kernel for you to select.                                                                                                                |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | |image32|                         | Code running status. |image33| indicates the code is being executed.                                                                     |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+

Monitoring Resources
--------------------

To obtain resource usage, select **Resource Monitor** in the right pane. The CPU usage and memory usage can be viewed.


.. figure:: /_static/images/en-us_image_0000001799338504.png
   :alt: **Figure 17** Resource usage

   **Figure 17** Resource usage

.. |image1| image:: /_static/images/en-us_image_0000001799338352.png
.. |image2| image:: /_static/images/en-us_image_0000001846137373.png
.. |image3| image:: /_static/images/en-us_image_0000001846057209.png
.. |image4| image:: /_static/images/en-us_image_0000001799498216.png
.. |image5| image:: /_static/images/en-us_image_0000001846137469.png
.. |image6| image:: /_static/images/en-us_image_0000001799338352.png
.. |image7| image:: /_static/images/en-us_image_0000001846137373.png
.. |image8| image:: /_static/images/en-us_image_0000001846057209.png
.. |image9| image:: /_static/images/en-us_image_0000001799498216.png
.. |image10| image:: /_static/images/en-us_image_0000001846137469.png
.. |image11| image:: /_static/images/en-us_image_0000001846057189.png
.. |image12| image:: /_static/images/en-us_image_0000001799338488.png
.. |image13| image:: /_static/images/en-us_image_0000001846137281.png
.. |image14| image:: /_static/images/en-us_image_0000001799498136.png
.. |image15| image:: /_static/images/en-us_image_0000001846137433.png
.. |image16| image:: /_static/images/en-us_image_0000001799338408.png
.. |image17| image:: /_static/images/en-us_image_0000001799498232.png
.. |image18| image:: /_static/images/en-us_image_0000001846137297.png
.. |image19| image:: /_static/images/en-us_image_0000001799338448.png
.. |image20| image:: /_static/images/en-us_image_0000001799498272.png
.. |image21| image:: /_static/images/en-us_image_0000001799498092.png
.. |image22| image:: /_static/images/en-us_image_0000001799338560.png
.. |image23| image:: /_static/images/en-us_image_0000001799498152.png
.. |image24| image:: /_static/images/en-us_image_0000001846057353.png
.. |image25| image:: /_static/images/en-us_image_0000001799338464.png
.. |image26| image:: /_static/images/en-us_image_0000001799338544.png
.. |image27| image:: /_static/images/en-us_image_0000001799498288.png
.. |image28| image:: /_static/images/en-us_image_0000001846137449.png
.. |image29| image:: /_static/images/en-us_image_0000001846057237.png
.. |image30| image:: /_static/images/en-us_image_0000001799338472.png
.. |image31| image:: /_static/images/en-us_image_0000001846137325.png
.. |image32| image:: /_static/images/en-us_image_0000001846057365.png
.. |image33| image:: /_static/images/en-us_image_0000001799338536.png
