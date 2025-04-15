:original_name: modelarts_30_0048.html

.. _modelarts_30_0048:

Cloning an open-source repository in GitHub
===========================================

Files can be cloned from a GitHub open-source repository to JupyterLab.

#. Use JupyterLab to open a running notebook instance.

#. Click |image1| in the navigation bar on the top of the JupyterLab window. In the displayed dialog box, click |image2| on the left to go to the page for cloning files from a GitHub open-source repository.


   .. figure:: /_static/images/en-us_image_0000001846136833.png
      :alt: **Figure 1** File upload icon

      **Figure 1** File upload icon


   .. figure:: /_static/images/en-us_image_0000001809489970.png
      :alt: **Figure 2** Page for cloning files from a GitHub open-source repository

      **Figure 2** Page for cloning files from a GitHub open-source repository

#. Enter a valid address of a GitHub open-source repository, select files from the displayed files and folders, and click **Clone**.

   GitHub open-source repository address: https://github.com/jupyterlab/extension-examples


   .. figure:: /_static/images/en-us_image_0000001856209405.png
      :alt: **Figure 3** Entering a valid address of a GitHub open-source repository

      **Figure 3** Entering a valid address of a GitHub open-source repository

#. The process is displayed during repository cloning. Wait until it is complete.


   .. figure:: /_static/images/en-us_image_0000001856210413.png
      :alt: **Figure 4** Process of cloning a repository

      **Figure 4** Process of cloning a repository

Error Handling
--------------

-  Failing to clone the repository may be caused by network issues. In this case, run the **git clone https://github.com/jupyterlab/extension-examples.git** command on the **terminal** page to test the network connectivity.
-  If the repository already exists in the current directory of the notebook instance, the system displays a message indicating that the repository name already exists. In this case, you can overwrite the existing repository or click |image3| to cancel the cloning.

.. |image1| image:: /_static/images/en-us_image_0000001799497612.png
.. |image2| image:: /_static/images/en-us_image_0000001846136841.png
.. |image3| image:: /_static/images/en-us_image_0000001799337812.jpg
