:original_name: modelarts_23_0209.html

.. _modelarts_23_0209:

Introduction to JupyterLab and Common Operations
================================================

JupyterLab is an interactive development environment. It is a next-generation product of Jupyter Notebook. JupyterLab enables you to compile notebooks, operate terminals, edit MarkDown text, open interaction modes, and view CSV files and images.

JupyterLab will be a mainstream development environment for developers. JupyterLab supports more flexible and powerful project operations, but has the same components as Jupyter Notebook.

ModelArts supports Jupyter Notebook and JupyterLab. You can use different tools to develop code in the same notebook instance.

Opening JupyterLab
------------------

#. Log in to the ModelArts management console. In the left navigation pane, choose **DevEnviron > Notebooks** to switch to the **Notebooks** page.
#. Select a notebook instance in the **Running** state and click **Open** in the **Operation** column to access the notebook instance.
#. On the **Jupyter** page, click **Open JupyterLab** in the upper right corner to access the JupyterLab page of the notebook instance.
#. The **Launcher** page is automatically displayed. You can use all open-source functions. For details, see `JupyterLab Documentation <https://jupyterlab.readthedocs.io/en/stable/>`__.

Creating and Opening a Notebook Instance
----------------------------------------

On the JupyterLab homepage, click an applicable AI engine in the **Notebook** area to create a notebook file with the selected framework.

The AI framework supported by each notebook instance varies according to the working environment. The following figure is only an example. Select an AI framework based on the site requirements. For details about all framework versions and Python versions supported by ModelArts, see :ref:`Supported AI Engines <en-us_topic_0000002043182276__en-us_topic_0000001846136609_en-us_topic_0162690357_section191109611479>`.

The created notebook file is displayed in the navigation pane on the left.

Creating a Notebook File and Opening the Console
------------------------------------------------

A console is essentially a Python terminal, which is similar to the native IDE of Python, displaying the output after a statement is entered.

On the JupyterLab homepage, click an applicable AI engine in the **Console** area to create a notebook file with the selected framework.

The AI framework supported by each notebook instance varies according to the working environment. The following figure is only an example. Select an AI framework based on the site requirements.

After the file is created, the console page is displayed.


.. figure:: /_static/images/en-us_image_0000002079103293.png
   :alt: **Figure 1** Creating a notebook file (console)

   **Figure 1** Creating a notebook file (console)

.. _en-us_topic_0000002043182264__en-us_topic_0000001799337328_en-us_topic_0208766071_section172463910383:

Uploading a File
----------------

On the JupyterLab page, you can click **Upload File** in the upper left corner and select a local file to upload.

The size of the file to be uploaded using this method is limited. If the file size exceeds the limit, use other methods to upload the file. For details, see :ref:`Uploading Data to JupyterLab <modelarts_23_0332>`.


.. figure:: /_static/images/en-us_image_0000002043024280.png
   :alt: **Figure 2** Uploading a file

   **Figure 2** Uploading a file

Editing a File
--------------

JupyterLab allows you to open multiple notebook instances or files (such as HTML, TXT, and Markdown files) in the same window and displays them on different tab pages.

Using JupyterLab, you can customize the display of multiple files. In the file display area on the right, you can drag a file to adjust its position. Multiple files can be concurrently displayed.


.. figure:: /_static/images/en-us_image_0000002079181933.png
   :alt: **Figure 3** Customized display of multiple files

   **Figure 3** Customized display of multiple files

When writing code in a notebook instance, you can create multiple views of a file to synchronously edit the file and view the execution result in real time.

To open multiple views, open the file and choose **File** > **New View for Notebook**.


.. figure:: /_static/images/en-us_image_0000002043024172.png
   :alt: **Figure 4** Multiple views of a file

   **Figure 4** Multiple views of a file

Downloading a File to a Local Computer
--------------------------------------

Files created in JupyterLab can be directly downloaded to a local computer. The size of the file to be downloaded using this method is limited. If the file size exceeds the limit, use other methods to download the file. For details, see :ref:`Downloading a File from JupyterLab <modelarts_23_0333>`.

In the JupyterLab file list, right-click the file to be downloaded and choose **Download** from the shortcut menu. The file is downloaded to the directory set for your browser.


.. figure:: /_static/images/en-us_image_0000002079181805.png
   :alt: **Figure 5** Downloading a file

   **Figure 5** Downloading a file

Common Icons and Plug-ins of JupyterLab
---------------------------------------


.. figure:: /_static/images/en-us_image_0000002079181917.png
   :alt: **Figure 6** Common icons and plug-ins of JupyterLab

   **Figure 6** Common icons and plug-ins of JupyterLab

.. table:: **Table 1** Icon description

   +----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Icon     | Description                                                                                                                                                       |
   +==========+===================================================================================================================================================================+
   | |image5| | Opens the Launcher page. Then you can quickly create notebook instances, consoles, or other files.                                                                |
   +----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | |image6| | Creates a folder.                                                                                                                                                 |
   +----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | |image7| | Uploads a file. For details, see :ref:`Uploading a File <en-us_topic_0000002043182264__en-us_topic_0000001799337328_en-us_topic_0208766071_section172463910383>`. |
   +----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | |image8| | Updates a folder.                                                                                                                                                 |
   +----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Common plug-ins in the plug-in area

   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
   | Plug-in                           | Description                                                                                                                               |
   +===================================+===========================================================================================================================================+
   | |image9|                          | Lists files. You can click here to display the list of all files in the notebook instance.                                                |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
   | |image10|                         | Lists ModelArts examples. You can click any example in the list to view its code and version mapping.                                     |
   |                                   |                                                                                                                                           |
   |                                   | ModelArts examples vary depending on regions. For details about the ModelArts examples available in a region, see the management console. |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
   | |image11|                         | Displays the terminals and kernels that are running in the current instance.                                                              |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
   | |image12|                         | Quick start command.                                                                                                                      |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
   | |image13|                         | Displays the tab page listing the files that are being opened.                                                                            |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
   | |image14|                         | Document organization.                                                                                                                    |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000002079181797.png
.. |image2| image:: /_static/images/en-us_image_0000002079181817.png
.. |image3| image:: /_static/images/en-us_image_0000002079103233.png
.. |image4| image:: /_static/images/en-us_image_0000002079103205.png
.. |image5| image:: /_static/images/en-us_image_0000002079181797.png
.. |image6| image:: /_static/images/en-us_image_0000002079181817.png
.. |image7| image:: /_static/images/en-us_image_0000002079103233.png
.. |image8| image:: /_static/images/en-us_image_0000002079103205.png
.. |image9| image:: /_static/images/en-us_image_0000002079103213.png
.. |image10| image:: /_static/images/en-us_image_0000002079103209.png
.. |image11| image:: /_static/images/en-us_image_0000002079103221.png
.. |image12| image:: /_static/images/en-us_image_0000002079181857.png
.. |image13| image:: /_static/images/en-us_image_0000002043182536.png
.. |image14| image:: /_static/images/en-us_image_0000002043182444.png
