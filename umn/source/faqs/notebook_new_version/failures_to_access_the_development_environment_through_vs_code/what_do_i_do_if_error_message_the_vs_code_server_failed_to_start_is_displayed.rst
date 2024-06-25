:original_name: modelarts_05_3119.html

.. _modelarts_05_3119:

What Do I Do If Error Message "The VS Code Server failed to start" Is Displayed?
================================================================================

Symptom
-------

|image1|

Solution
--------

#. Check whether the VS Code version is 1.65.0 or later. If so, check the Remote-SSH version. If the version is earlier than 0.76.1, upgrade Remote-SSH.

   |image2|

#. Open the command panel (**Ctrl+Shift+P** for Windows and **Cmd+Shift+P** for macOS), search for **Kill VS Code Server on Host**, and locate the affected instance, which will be automatically cleared. Then, establish the connection again.


   .. figure:: /_static/images/en-us_image_0000001943978289.png
      :alt: **Figure 1** Clearing the affected instance

      **Figure 1** Clearing the affected instance

.. |image1| image:: /_static/images/en-us_image_0000001910059122.png
.. |image2| image:: /_static/images/en-us_image_0000001910059118.png
