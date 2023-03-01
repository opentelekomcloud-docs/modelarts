:original_name: modelarts_23_0337.html

.. _modelarts_23_0337:

Setting the Initialization Script
=================================

When using a notebook instance for development, users often install some software. However, after the notebook instance is stopped and then restarted, the software needs to be reinstalled, which affects the efficiency. The function of setting the boot initialization script is added to JupyterLab of DevEnviron. You can integrate the package installation operations into the script and set the script as the boot initialization script. Then, this script is executed by default each time the notebook instance is started, improving the development efficiency.

Prerequisites
-------------

The script has been encoded in JupyterLab.

Constraints
-----------

Package installation operations that must be performed by the **root** user, for example, **apt-get** package installation, cannot be performed.

Setting the Script
------------------

#. In JupyterLab, right-click an edited script and choose **Set as Initialization Script** from the shortcut menu to set the script as the initialization script for starting the instance.


   .. figure:: /_static/images/en-us_image_0000001454986153.png
      :alt: **Figure 1** Set as Initialization Script

      **Figure 1** Set as Initialization Script

#. If the message "Config Succeed" is displayed, the setting is successful.


   .. figure:: /_static/images/en-us_image_0000001404666346.png
      :alt: **Figure 2** Successful setting

      **Figure 2** Successful setting

Viewing and Updating the Initialization Script
----------------------------------------------

#. On the menu bar, choose **Settings** > **Advanced Setting Editor**.

   Alternatively, use the default shortcut key **Ctrl+** to view the script.


   .. figure:: /_static/images/en-us_image_0000001404986170.png
      :alt: **Figure 3** Advanced settings page of JupyterLab

      **Figure 3** Advanced settings page of JupyterLab

   You can view the initialization script in the view on the right.


   .. figure:: /_static/images/en-us_image_0000001455145977.png
      :alt: **Figure 4** Viewing the set initialization script

      **Figure 4** Viewing the set initialization script

#. Edit the **scriptFile** content in **User Preferences** and click the save button in the upper right corner to update the initialization script.


   .. figure:: /_static/images/en-us_image_0000001404826194.png
      :alt: **Figure 5** Updating the initialization script

      **Figure 5** Updating the initialization script

Executing the Initialization Script
-----------------------------------

After the initialization script is set, the script is executed by default when the notebook instance is started.

-  If the operation is successful, a success message is displayed in the lower right corner.

-  If the execution fails, a dialog box is displayed. You can click **View logs** to view the logs.


   .. figure:: /_static/images/en-us_image_0000001404666342.png
      :alt: **Figure 6** Execution failed

      **Figure 6** Execution failed
