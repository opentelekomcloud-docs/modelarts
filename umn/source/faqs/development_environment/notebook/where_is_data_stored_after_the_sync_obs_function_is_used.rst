.. _modelarts_05_0081:

Where Is Data Stored After the Sync OBS Function Is Used?
=========================================================

#. Log in to the ModelArts management console, and choose **DevEnviron > Notebooks**.

#. In the **Operation** column of the target notebook instance in the notebook list, click **Open** to go to the **Jupyter** page.

#. On the **Files** tab page of the **Jupyter** page, select the target file and click **Sync OBS** in the upper part of the page to synchronize the file. The file is stored in the **~/work** directory of the instance.

#. On the **Files** tab page of the **Jupyter** page, click **New** and select **Terminal**. The **Terminal** page is displayed.

#. Run the following command to go to the **~/work** directory.

   .. code-block::

      cd work

#. Run the **ls** command in the **~/work** directory to view the files.
