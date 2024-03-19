:original_name: modelarts_30_0023.html

.. _modelarts_30_0023:

Changing an IP Address for Remotely Accessing a Notebook Instance
=================================================================

During the creation of a notebook instance, if you set a whitelist for remotely accessing it, you can change the IP addresses in the whitelist on the notebook instance details page.

#. Log in to the ModelArts management console. Choose **DevEnviron** > **Notebook** in the navigation pane on the left. The notebook list of the new version is displayed.

#. Click the name of an instance to go to its details page. Click |image1| on the right of the whitelist to change the IP addresses that are allowed to remotely access the notebook instance. After the modification, click |image2|.

   Ensure that public IP addresses are set. If your source device and the ModelArts are isolated from each other in network, obtain the public IP address of your source device using a mainstream search engine, for example, by entering "IP address lookup", but not by running **ipconfig** or **ifconfigip** locally.

#. After you change the IP addresses, the existing links are still valid. After the links are released, the new links only from the changed IP addresses can be set up.

.. |image1| image:: /_static/images/en-us_image_0000001846137217.png
.. |image2| image:: /_static/images/en-us_image_0000001846057129.png
