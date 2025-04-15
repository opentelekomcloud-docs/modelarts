:original_name: modelarts_05_3118.html

.. _modelarts_05_3118:

What Do I Do If a Remote Connection Is in the Retry State?
==========================================================

Symptom
-------

|image1|

Possible Cause
--------------

Downloading the VS Code server failed before, leading to residual data. As a result, new download cannot be performed.

Solution
--------

Method 1 (performed locally): Open the command panel (**Ctrl+Shift+P** for Windows and **Cmd+Shift+P** for macOS), search for **Kill VS Code Server on Host**, and locate the affected instance, which will be automatically cleared. Then, establish the connection again.


.. figure:: /_static/images/en-us_image_0000002268820529.png
   :alt: **Figure 1** Clearing the affected instance

   **Figure 1** Clearing the affected instance

Method 2 (performed remotely): Delete the files that are being used in **/home/ma-user/.vscode-server/bin/** on the VS Code terminal. Then, establish the connection again.

.. code-block::

   ssh -tt -o StrictHostKeyChecking=no -i ${IdentityFile} ${User}@${HostName} -p ${Port}
   rm -rf /home/ma-user/.vscode-server/bin/

Parameters:

- **IdentityFile**: Path to the local key

- **User**: Username, for example, **ma-user**

- **HostName**: IP address

- **Port**: Port number

.. note::

   The preceding methods can also be used to resolve issues related to the VS Code server.

.. |image1| image:: /_static/images/en-us_image_0000002268740613.png
