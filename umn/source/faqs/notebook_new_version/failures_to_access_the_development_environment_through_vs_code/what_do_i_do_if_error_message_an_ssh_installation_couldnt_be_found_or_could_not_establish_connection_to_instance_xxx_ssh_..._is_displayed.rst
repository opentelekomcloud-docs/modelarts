:original_name: modelarts_05_3123.html

.. _modelarts_05_3123:

What Do I Do If Error Message "An SSH installation couldn't be found" or "Could not establish connection to instance xxx: 'ssh' ..." Is Displayed?
==================================================================================================================================================

Symptom
-------

|image1|

Or

|image2|

When VS Code attempts to access a notebook instance, the system always prompts you to select a certificate, and the message, excepting the title, consists of garbled characters. After the certificate is selected, the system still does not respond and the connection failed.

Possible Cause
--------------

OpenSSH is not installed in the current environment or is not installed in the default path. For details, see the `VS Code document <https://code.visualstudio.com/docs/remote/troubleshooting#_installing-a-supported-ssh-client>`__.

Solution
--------

-  If OpenSSH is not installed in the current environment, `download and install it <https://code.visualstudio.com/docs/remote/troubleshooting#_installing-a-supported-ssh-client>`__.

   |image3|

If OpenSSH fails to be installed, manually `download the OpenSSH installation package <https://github.com/PowerShell/Win32-OpenSSH/releases>`__ and perform the following operations:

#. Download the .zip package and decompress it into **C:\\Windows\\System32**.

#. In **C:\\Windows\\System32\\OpenSSH-xx**, open CMD as the administrator and run the following command:

   .. code-block::

       powershell.exe -ExecutionPolicy Bypass -File install-sshd.ps1

#. Add **C:\\Program Files\\OpenSSH-xx** (in which the SSH executable .exe file is stored) to environment system variables.

#. Open CMD again and run **ssh**. If the following information is displayed, the installation is successful. Otherwise, go to :ref:`5 <en-us_topic_0000002079183385__li9295193011380>` and :ref:`6 <en-us_topic_0000002079183385__li194921423153911>`.

   |image4|

#. .. _en-us_topic_0000002079183385__li9295193011380:

   Enable port 22 (default OpenSSH port) on the firewall and run the following command in Command Prompt:

   .. code-block::

       netsh advfirewall firewall add rule name=sshd dir=in action=allow protocol=TCP localport=22

#. .. _en-us_topic_0000002079183385__li194921423153911:

   Run the following command to start OpenSSH:

   .. code-block::

       Start-Service sshd

-  If OpenSSH is not installed in the default path, open the command panel (**Ctrl+Shift+P** for Windows and **Cmd+Shift+P** for macOS).

   Search for **Open settings**.

   |image5|

   Add **remote.SSH.path** to **settings.json**, for example, **"remote.SSH.path": "Installation path of the local OpenSSH"**.

   |image6|

.. |image1| image:: /_static/images/en-us_image_0000002079183657.png
.. |image2| image:: /_static/images/en-us_image_0000002079105085.png
.. |image3| image:: /_static/images/en-us_image_0000002043026016.png
.. |image4| image:: /_static/images/en-us_image_0000002079105093.png
.. |image5| image:: /_static/images/en-us_image_0000002079183661.png
.. |image6| image:: /_static/images/en-us_image_0000002043184352.png
