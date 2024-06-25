:original_name: modelarts_30_0038.html

.. _modelarts_30_0038:

Configuring a Local IDE Accessed Using SSH
==========================================

This section describes how to use PuTTY to remotely log in to a notebook instance on the cloud in the Windows environment.

Prerequisites
-------------

-  You have created a notebook instance with remote SSH enabled and whitelist configured. Ensure that the instance is running. For details, see :ref:`Creating a Notebook Instance <modelarts_30_0004>`.

-  The address and port number of the development environment are available. To obtain this information, go to the notebook instance details page.


   .. figure:: /_static/images/en-us_image_0000001809617018.png
      :alt: **Figure 1** Instance details page

      **Figure 1** Instance details page

-  The key pair is available.

   A key pair is automatically downloaded after you create it. Securely store your key pair. If an existing key pair is lost, create a new one.

Step 1 Install the SSH Tool
---------------------------

`Download <https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html>`__ and install the SSH remote connection tool, for example, PuTTY.

.. _en-us_topic_0000001799496572__section97911985211:

Step 2 Use PuTTYgen to Convert the .pem Key Pair File to a .ppk Key Pair File
-----------------------------------------------------------------------------

#. `Download PuTTYgen <https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html>`__ and double-click it to run it.

#. Click **Load** to load the .pem key file created and saved during notebook instance creation.

#. Click **Save private key** to save the generated .ppk file. The file name can be customized, for example, **key.ppk**.


   .. figure:: /_static/images/en-us_image_0000001799338312.png
      :alt: **Figure 2** Converting the .pem key pair file to a .ppk key pair file

      **Figure 2** Converting the .pem key pair file to a .ppk key pair file

Step 3 Use SSH to Connect to a Notebook Instance
------------------------------------------------

#. Run PuTTY.

#. Click **Session** and set the following parameters:

   a. **Host Name (or IP address)**: address for accessing the in-cloud notebook instance. Obtain the address on the page providing detailed information of the target notebook instance,
   b. **Port**: port number for accessing the in-cloud notebook instance. Obtain the port number on the page providing detailed information of the target notebook instance, for example, **32701**.
   c. **Connection type**: **SSH**
   d. **Saved Sessions**: task name, which can be clicked for remote connection when you use PuTTY next time


   .. figure:: /_static/images/en-us_image_0000001799498076.png
      :alt: **Figure 3** Configuring **Session**

      **Figure 3** Configuring **Session**

#. Choose **Window** > **Translation** and select **UTF-8** from the drop-down list box in the **Remote character set** area.


   .. figure:: /_static/images/en-us_image_0000001846057169.png
      :alt: **Figure 4** Setting the character format

      **Figure 4** Setting the character format

#. Choose **Connection** > **Data** and enter **ma-user** for **Auto-login username**.


   .. figure:: /_static/images/en-us_image_0000001846137225.png
      :alt: **Figure 5** Entering a username

      **Figure 5** Entering a username

#. Choose **Connection** > **SSH** > **Auth**, click **Browse**, and select the .ppk file generated in :ref:`step 2 <en-us_topic_0000001799496572__section97911985211>`.

   |image1|

#. Click **Open**. If you are logging in to the instance for the first time, PuTTY displays a security warning dialog box, asking if you want to accept the instance security certificate. Click **Accept** to save the certificate to your local registry.


   .. figure:: /_static/images/en-us_image_0000001799338300.png
      :alt: **Figure 6** Asking if you want to accept the instance security certificate

      **Figure 6** Asking if you want to accept the instance security certificate

#. Connect to the notebook instance.


   .. figure:: /_static/images/en-us_image_0000001799338336.png
      :alt: **Figure 7** Connecting to a notebook instance

      **Figure 7** Connecting to a notebook instance

.. |image1| image:: /_static/images/en-us_image_0000001799498084.png
