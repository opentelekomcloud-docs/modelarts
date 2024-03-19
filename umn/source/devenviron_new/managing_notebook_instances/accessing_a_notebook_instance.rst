:original_name: modelarts_30_0005.html

.. _modelarts_30_0005:

Accessing a Notebook Instance
=============================

Access a notebook instance in the **Running** state for coding.

The methods of accessing notebook instances vary depending on the AI engine based on which the instance was created.

-  Accessed online using JupyterLab. For details, see :ref:`Using JupyterLab to Develop Models <modelarts_30_0007>`.
-  Remotely accessed from a local IDE through SSH. For details, see :ref:`Configuring a Local IDE Accessed Using SSH <modelarts_30_0038>`.

A ModelArts notebook instance is started as user **ma-user**. The default working directory of the instance is **/home/ma-user**.

|image1|

Create an instance and mount the persistent storage to **/home/ma-user/work**.

|image2|

The data stored in the **work** directory only is retained after the instance is stopped or restarted. When you use a development environment, store the data for persistence in **/home/ma-user/work**.

.. |image1| image:: /_static/images/en-us_image_0000001799498028.png
.. |image2| image:: /_static/images/en-us_image_0000001846057113.png
