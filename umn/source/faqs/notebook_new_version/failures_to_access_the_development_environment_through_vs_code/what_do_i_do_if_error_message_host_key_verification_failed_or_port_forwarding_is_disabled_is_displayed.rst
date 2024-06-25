:original_name: modelarts_05_3128.html

.. _modelarts_05_3128:

What Do I Do If Error Message "Host key verification failed" or "Port forwarding is disabled" Is Displayed?
===========================================================================================================

Symptom
-------

|image1|

Or

|image2|

Possible Cause
--------------

After the notebook instance is restarted, its public key changes. The alarm is generated when OpenSSH detected the key change.

Solution
--------

-  Add **-o StrictHostKeyChecking=no** for remote access through the CLI in VS Code.

   .. code-block::

      ssh -tt -o StrictHostKeyChecking=no -i ${IdentityFile} ${User}@${HostName} -p ${Port}

   Parameters:

   - **IdentityFile**: Path to the local key

   - **User**: Username, for example, **ma-user**

   - **HostName**: IP address

   - **Port**: Port number

-  Add **StrictHostKeyChecking no** and **UserKnownHostsFile=/dev/null** to the local **ssh config** file for manual configuration of remote access in VS Code.

   .. code-block::

      Host xxx
          HostName x.x.x.x # IP address
          Port 22522
          User ma-user
          IdentityFile C:/Users/my.pem
          StrictHostKeyChecking no
          UserKnownHostsFile=/dev/null
          ForwardAgent yes

Note that SSH logins will be insecure after the preceding parameters are added because the **known_hosts** file will be ignored during the logins.

.. |image1| image:: /_static/images/en-us_image_0000001910019094.png
.. |image2| image:: /_static/images/en-us_image_0000001910059110.png
