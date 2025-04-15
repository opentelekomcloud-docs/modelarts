:original_name: modelarts_05_3168.html

.. _modelarts_05_3168:

What Do I Do for an Automatically Disconnected VS Code Connection If No Operation Is Performed for a Long Time?
===============================================================================================================

Symptom
-------

After an SSH connection is set up through VS Code, no operation is performed for a long time and the window retains open. When the connection is used again, it is found that the connection is disconnected and no error message is displayed.

According to VS Code Remote-SSH logs, the connection was disconnected about two hours after the setup.

|image1|

Possible Cause
--------------

After SSH interaction stops for a period of time, the firewall disconnects idle connections (http://bluebiu.com/blog/linux-ssh-session-alive.html). The default SSH configuration does not lead to a proactive disconnection upon timeout. Since the instance runs stably on the backend, set up the connection again to resolve this issue.

Solution
--------

To retain connections if no operation is performed for a long time, configure periodic message sending through SSH. In this way, the connection will not become idle on the firewall.

-  Configure the client as needed. If the client is not configured, no heartbeat packet will be sent to the server by default.


   .. figure:: /_static/images/en-us_image_0000002268821633.png
      :alt: **Figure 1** Opening the VS Code SSH configuration file

      **Figure 1** Opening the VS Code SSH configuration file


   .. figure:: /_static/images/en-us_image_0000002268741729.png
      :alt: **Figure 2** Adding configurations

      **Figure 2** Adding configurations

   The configuration is as follows:

   .. code-block::

      Host ModelArts-xx
          ...
          ServerAliveInterval 3600  # Add this configuration in the unit of second, indicating that the client will actively send a heartbeat packet to the server every hour.
          ServerAliveCountMax 3  # Add this configuration, indicating that if the server does not respond after the heartbeat packet is sent for three times, the connection will be disconnected.

   For example, if the firewall is configured to disconnect a connection if the connection is idle for two hours, set **ServerAliveInterval** to a value less than two hours (for example, one hour) on the client to prevent the firewall from disconnecting the connection.

-  Configure the server in **/home/ma-user/.ssh/etc/sshd_config**. (Notebook has been configured, and 24 hours is longer than the time configured on the firewall for disconnecting connections. This configuration does not need to be manually modified. It is only used to help understand the SSH configuration.)

   |image2|

   The preceding configuration shows that the server actively sends a heartbeat packet to the client every 24 hours, and the connection will be disconnected if the client does not respond after the heartbeat packet is sent for three times.

   For details, see https://unix.stackexchange.com/questions/3026/what-do-options-serveraliveinterval-and-clientaliveinterval-in-sshd-config-d.

-  If a connection must be consistently retained, it is a good practice to write logs in a separate log file and run the script on the backend. For example:

   .. code-block::

      nohup train.sh > output.log 2>&1 & tail -f output.log

.. |image1| image:: /_static/images/en-us_image_0000002268821637.png
.. |image2| image:: /_static/images/en-us_image_0000002268741737.png
