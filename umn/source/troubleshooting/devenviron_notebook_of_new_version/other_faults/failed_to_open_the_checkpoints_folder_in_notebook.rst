:original_name: modelarts_05_3171.html

.. _modelarts_05_3171:

Failed to Open the checkpoints Folder in Notebook
=================================================

**checkpoints** is a keyword in notebook. If a created folder is named **checkpoints**, the folder will not be opened, renamed, or deleted on JupyterLab.


.. figure:: /_static/images/en-us_image_0000002079182965.png
   :alt: **Figure 1** checkpoints

   **Figure 1** checkpoints

**Procedure**

Open the terminal and perform operations using the CLI.

#. Run the **mkdir** *xxx* command to create a folder, in which *xxx* is the folder name. Do not use **checkpoints** to name the folder.

#. Move the data in the **checkpoints** folder to the new folder and delete the **checkpoints** folder in the root directory.

   .. code-block::

      mv checkpoints/* xxx
      rm -r checkpoints
