:original_name: modelarts_05_0082.html

.. _modelarts_05_0082:

How Do I View GPU Usage on the Notebook?
========================================

If you select GPU when creating a notebook instance, perform the following operations to view GPU usage:

#. Log in to the ModelArts management console, and choose **DevEnviron > Notebooks**.

#. In the **Operation** column of the target notebook instance in the notebook list, click **Open** to go to the **Jupyter** page.

#. On the **Files** tab page of the **Jupyter** page, click **New** and select **Terminal**. The **Terminal** page is displayed.

#. Run the following command to view GPU usage:

   .. code-block::

      nvidia-smi

#. Check which processes in the current notebook instance use GPUs.

   Method 1:

   .. code-block::

      python /modelarts/tools/gpu_processes.py

   The following figure shows the case that the current process is using GPUs.

   |image1|

   The following figure shows the case that the current process is not using GPUs.

   |image2|

   Method 2:

   Open **/resource_info/gpu_usage.json** and view the processes that are using GPUs.

   |image3|

   If no process is using GPUs, the file may be unavailable or empty.

.. |image1| image:: /_static/images/en-us_image_0000002079105041.png
.. |image2| image:: /_static/images/en-us_image_0000002079105037.png
.. |image3| image:: /_static/images/en-us_image_0000002043184304.png
