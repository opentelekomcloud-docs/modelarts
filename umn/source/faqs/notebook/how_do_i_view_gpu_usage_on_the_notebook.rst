:original_name: modelarts_21_0072.html

.. _modelarts_21_0072:

How Do I View GPU Usage on the Notebook?
========================================

If you select GPU when creating a notebook instance, perform the following operations to view GPU usage:

#. Log in to the ModelArts management console, and choose **DevEnviron > Notebooks**.

#. In the **Operation** column of the target notebook instance in the notebook list, click **Open** to go to the **Jupyter** page.

#. On the **Files** tab page of the **Jupyter** page, click **New** and select **Terminal**. The **Terminal** page is displayed.

#. Run the following command to view GPU usage:

   .. code-block::

      nvidia-smi
