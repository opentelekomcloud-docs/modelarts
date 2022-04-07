.. _modelarts_23_0120:

Common Operations on Jupyter Notebook
=====================================

This section describes common operations on Jupyter Notebook.

Opening Jupyter Notebook
------------------------

In the notebook instance list, locate the row where the target notebook instance resides and click **Open** in the **Operation** column to switch to the **Jupyter Notebook** page.

Two tab pages are available on the **Jupyter Notebook** page: **Files** and **Running**.

.. _modelarts_23_0120__en-us_topic_0188347008_fig13203124195913:

.. figure:: /_static/images/en-us_image_0000001110761034.png
   :alt: **Figure 1** Jupyter Notebook


   **Figure 1** Jupyter Notebook

Selecting Different AI Engines to Create Files
----------------------------------------------

Open a notebook instance and go to the **Jupyter Notebook** page. On the **Files** tab page, click **New** in the upper right corner, select the required AI engine, and create a file for encoding.

.. _modelarts_23_0120__en-us_topic_0188347008_fig8224175513165:

.. figure:: /_static/images/en-us_image_0000001157080885.png
   :alt: **Figure 2** Selecting different AI engines


   **Figure 2** Selecting different AI engines

Uploading a File
----------------

Open a notebook instance and go to the **Jupyter Notebook** page. On the **Files** tab page, click **Upload** in the upper right corner to select a file from the local PC and upload it.

.. _modelarts_23_0120__en-us_topic_0188347008_fig89015882019:

.. figure:: /_static/images/en-us_image_0000001110920940.png
   :alt: **Figure 3** Uploading a file


   **Figure 3** Uploading a file

Compiling a File
----------------

After a file is created, click the file name to go to the file compilation page.

.. _modelarts_23_0120__en-us_topic_0188347008_fig65191088443:

.. figure:: /_static/images/en-us_image_0000001110920938.png
   :alt: **Figure 4** Compiling a file


   **Figure 4** Compiling a file

.. table:: **Table 1** Introduction to the file compilation page

   +-----------------------+------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | No.                   | Area                         | Description                                                                                                                                                                                                                                                                                                                                                                                                                 |
   +=======================+==============================+=============================================================================================================================================================================================================================================================================================================================================================================================================================+
   | 1                     | File name                    | You can enter a user-defined file name in this area. After the file name is changed and saved, the new file name is updated to the file list accordingly.                                                                                                                                                                                                                                                                   |
   +-----------------------+------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 2                     | Menu bar                     | The menu bar provides rich functions such as File, Edit, View, Insert, Cell, Kernel, and Help. For details, see `Jupyter Notebook Documentation <https://jupyter.org/documentation>`__. The following toolbar provides common functions for compiling common Python running files.                                                                                                                                          |
   +-----------------------+------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 3                     | Toolbar                      | The toolbar lists the common shortcut operations. From left to right, the shortcut operations are as follows: saving a file, adding a new cell, cutting a selected cell, copying a selected cell, pasting a selected cell, moving a selected cell upwards, moving a selected cell downwards, running a selected cell, terminating the kernel, restarting the kernel, and restarting the kernel and running all cells again. |
   |                       |                              |                                                                                                                                                                                                                                                                                                                                                                                                                             |
   |                       |                              | The **Code** drop-down list contains the following options:                                                                                                                                                                                                                                                                                                                                                                 |
   |                       |                              |                                                                                                                                                                                                                                                                                                                                                                                                                             |
   |                       |                              | -  Code: Write Python code.                                                                                                                                                                                                                                                                                                                                                                                                 |
   |                       |                              | -  MarkDown: Write MarkDown code, which is usually used for comments.                                                                                                                                                                                                                                                                                                                                                       |
   |                       |                              | -  Raw NBConvert: conversion tool.                                                                                                                                                                                                                                                                                                                                                                                          |
   |                       |                              | -  Heading: Quickly add a MarkDown title.                                                                                                                                                                                                                                                                                                                                                                                   |
   +-----------------------+------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 4                     | AI engine and Python version | Displays the AI engine and Python version corresponding to the current file. For details about all AI engines and Python versions supported by ModelArts, see :ref:`Supported AI Engines <modelarts_23_0033__en-us_topic_0162690357_section191109611479>`.                                                                                                                                                                  |
   +-----------------------+------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 5                     | Code cell                    | Each cell has two modes: command mode and editing mode.                                                                                                                                                                                                                                                                                                                                                                     |
   |                       |                              |                                                                                                                                                                                                                                                                                                                                                                                                                             |
   |                       |                              | The blue bar on the left indicates the command mode, and the green bar indicates the editing mode (in this mode, the cursor exists in the cell and you can write code). In command mode, you can press **Enter** or click the code box to enter the editing mode. In editing mode, you can press **ESC** or click the left area of the code box to enter the command mode.                                                  |
   |                       |                              |                                                                                                                                                                                                                                                                                                                                                                                                                             |
   |                       |                              | |image1|                                                                                                                                                                                                                                                                                                                                                                                                                    |
   +-----------------------+------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Deleting a File or Folder
-------------------------

To delete a file or folder from Jupyter Notebook, select the file or folder in the **Files** list and click the **Delete** button.

.. note::

   After the file or folder is deleted, click the **Refresh** button in the upper right corner to refresh the Jupyter page and clear the cache.

.. _modelarts_23_0120__en-us_topic_0188347008_fig10721575216:

.. figure:: /_static/images/en-us_image_0000001110761038.png
   :alt: **Figure 5** Jupyter page


   **Figure 5** Jupyter page

.. |image1| image:: /_static/images/en-us_image_0000001110920936.png

