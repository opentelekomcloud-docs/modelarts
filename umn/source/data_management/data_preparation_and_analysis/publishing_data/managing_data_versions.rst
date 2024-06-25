:original_name: dataprepare-modelarts-0029.html

.. _dataprepare-modelarts-0029:

Managing Data Versions
======================

During data preparation, you can publish data into multiple versions for dataset management. You can view version updates, set the current version, and delete versions.

Viewing Dataset Version Updates
-------------------------------

#. Log in to the ModelArts management console. In the left navigation pane, choose **Data Management** > **Datasets**.

#. In the dataset list, choose **More > Manage Version** in the **Operation** column. The **Manage Version** tab page is displayed.

   You can view basic information about the dataset, and view the versions and publish time on the left.


   .. figure:: /_static/images/en-us_image_0000001943972257.png
      :alt: **Figure 1** Viewing dataset versions

      **Figure 1** Viewing dataset versions

Setting to Current Version
--------------------------

#. Log in to the ModelArts management console. In the left navigation pane, choose **Data Management** > **Datasets**.
#. In the dataset list, choose **More > Manage Version** in the **Operation** column. The **Manage Version** tab page is displayed.
#. On the **Manage Version** tab page, select the desired dataset version, and click **Set to Current Version** in the basic information area on the right. After the setting is complete, **Current version** is displayed to the right of the version name.

   .. note::

      Only the version in **Normal** status can be set to the current version.

Deleting a Dataset Version
--------------------------

#. Log in to the ModelArts management console. In the left navigation pane, choose **Data Management** > **Datasets**.
#. In the dataset list, choose **More > Manage Version** in the **Operation** column. The **Manage Version** tab page is displayed.
#. Locate the row that contains the target version, and click **Delete** in the **Operation** column. In the dialog box that is displayed, click **OK**.

   .. note::

      Deleting a dataset version does not remove the original data. Data and its labeling information are still stored in the OBS directory. However, this affects version management. Exercise caution when performing this operation.
