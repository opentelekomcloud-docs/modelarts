:original_name: modelarts_05_0373.html

.. _modelarts_05_0373:

Why Does the System Display a Message Indicating My Label Fails to Save on ModelArts?
=====================================================================================

Symptom
-------

Take the Google Chrome browser as an example. When an image is labeled for the first time, the system displays a message in the upper right corner, indicating that the label fails to save. But when the same image is labeled the second time, a message is displayed, indicating that the label is saved. This issue occurs occasionally. When this issue occurs, the request status is **(failed)net::ERR\_**\ *ADDRESS\_*\ **IN_USE**, which is obtained by pressing **F12** on the Google Chrome browser and clicking **Network**.

|image1|

Possible Cause
--------------

The local network is faulty, for example, the network is unstable, or the network configuration is incorrect.

Solution
--------

-  Switch to a stable network and try again.
-  Initialize the network configuration. To do so, start **cmd** as the administrator, run the **netsh winsock reset** command, and restart the computer. Then, log in to the data labeling platform again.

.. |image1| image:: /_static/images/en-us_image_0000002079104885.png
