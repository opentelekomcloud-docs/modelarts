:original_name: modelarts_05_0021.html

.. _modelarts_05_0021:

What Do I Do If I Cannot Access My Notebook Instance?
=====================================================

Troubleshoot the issue based on error code.

Error 404
---------

If this error is reported when an IAM user creates an instance, the IAM user does not have the permissions to access the corresponding storage location (OBS bucket).

Solution

#. Log in to the OBS console using the primary account and grant access permissions for the OBS bucket to the IAM user.
#. After the IAM user obtains the permissions, log in to the ModelArts console, delete the instance, and use the OBS path to create a notebook instance.

Error 503
---------

If this error is reported, it is possible that the instance is consuming too many resources. If this is the case, stop the instance and restart it.

Error 500
---------

Notebook JupyterLab cannot be opened, and error 500 is reported. The possible cause is that the disk space in the **work** directory is used up. In this case, identify the fault cause and clear the disk by referring to .

Error "This site can't be reached"
----------------------------------

After a notebook instance is created, click **Open** in the **Operation** column. The error message shown in the following figure is displayed.

|image1|

Do as follows to resolve this issue: Copy the domain name of the page , add it to the **Do not use proxy server for addresses beginning with** text box, and save the settings.

.. |image1| image:: /_static/images/en-us_image_0000001943979113.png
