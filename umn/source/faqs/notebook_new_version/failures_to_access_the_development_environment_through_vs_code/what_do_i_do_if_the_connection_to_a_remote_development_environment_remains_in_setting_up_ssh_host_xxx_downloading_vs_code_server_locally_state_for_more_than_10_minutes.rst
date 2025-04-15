:original_name: modelarts_05_3117.html

.. _modelarts_05_3117:

What Do I Do If the Connection to a Remote Development Environment Remains in "Setting up SSH Host xxx: Downloading VS Code Server locally" State for More Than 10 Minutes?
===========================================================================================================================================================================

Symptom
-------

|image1|

Possible Cause
--------------

The local network is faulty. As a result, it takes a long time to automatically install the VS Code server remotely.

Solution
--------

Manually install the VS Code server.

#. .. _en-us_topic_0000002268820025__li11183911182410:

   Obtain the VS Code commit ID.

   |image2|

#. Download the VS Code server package of the required version. Select Arm or x86 based on the CPU architecture of the development environment.

   .. note::

      Replace *${commitID}* in the following link with the commit ID obtained in :ref:`1 <en-us_topic_0000002268820025__li11183911182410>`.

   -  For Arm, download **vscode-server-linux-arm64.tar.gz**.

      https://update.code.visualstudio.com/commit:${commitID}/server-linux-arm64/stable

   -  For x86, download **vscode-server-linux-x64.tar.gz**.

      https://update.code.visualstudio.com/commit:${commitID}/server-linux-x64/stable

#. Access the remote environment.

   Switch to **Terminal** in VS Code.

   |image3|

   Run the following command in VS Code Terminal to access the remote development environment:

   .. code-block::

      ssh -tt -o StrictHostKeyChecking=no -i ${IdentityFile} ${User}@${HostName} -p ${Port}

   Parameters:

   - **IdentityFile**: Path to the local key

   - **User**: Username, for example, **ma-user**

   - **HostName**: IP address

   - **Port**: Port number

   |image4|

#. Manually install the VS Code server.

   Run the following commands on the VS Code terminal to clear the residual data (replace *${commitID}* in the commands with the commit ID obtained in :ref:`1 <en-us_topic_0000002268820025__li11183911182410>`):

   .. code-block::

      rm -rf /home/ma-user/.vscode-server/bin/${commitID}/*
      mkdir -p /home/ma-user/.vscode-server/bin/${commitID}

   Upload the VS Code server package to the development environment.

   .. code-block::

      exit
      scp -i xxx.pem -P 31205 Local path to the VS Code server package ma-user@xxx:/home/ma-user/.vscode-server/bin

   .. code-block::

      ssh -tt -o StrictHostKeyChecking=no -i ${IdentityFile} ${User}@${HostName} -p ${Port}

   Parameters:

   - **IdentityFile**: Path to the local key

   - **User**: Username, for example, **ma-user**

   - **HostName**: IP address

   - **Port**: Port number

   Take Arm as an example. Decompress the VS Code server package to **$HOME/.vscode-server/bin**. Replace *${commitID}* in the command with the commit ID obtained in :ref:`1 <en-us_topic_0000002268820025__li11183911182410>`.

   .. code-block::

      cd /home/ma-user/.vscode-server/bin
      tar -zxf vscode-server-linux-arm64.tar.gz
      mv vscode-server-linux-arm64/* ${commitID}

#. Establish the remote connection again.

.. |image1| image:: /_static/images/en-us_image_0000002268821017.png
.. |image2| image:: /_static/images/en-us_image_0000002233901680.png
.. |image3| image:: /_static/images/en-us_image_0000002268741137.png
.. |image4| image:: /_static/images/en-us_image_0000002268741113.png
