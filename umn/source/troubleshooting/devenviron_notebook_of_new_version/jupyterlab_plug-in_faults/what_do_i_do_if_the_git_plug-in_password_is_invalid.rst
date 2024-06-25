:original_name: modelarts_13_0256.html

.. _modelarts_13_0256:

What Do I Do If the Git Plug-in Password Is Invalid?
====================================================

Symptom
-------

If the Git plug-in is used in JupyterLab, when a private repository is cloned or a file is pushed, an error occurs.


.. figure:: /_static/images/en-us_image_0000001909848908.png
   :alt: **Figure 1** JupyterLab

   **Figure 1** JupyterLab


.. figure:: /_static/images/en-us_image_0000001910008924.png
   :alt: **Figure 2** Error

   **Figure 2** Error

Possible Causes
---------------

The authorization using a password has been canceled in GitHub. When cloning a private repository or pushing a file, you are required to enter a token in the authorization text box.

Solution
--------

Use a token for authorization. When cloning a private repository or pushing a file, enter the token in the authorization text box.


.. figure:: /_static/images/en-us_image_0000001909848912.png
   :alt: **Figure 3** token

   **Figure 3** token
