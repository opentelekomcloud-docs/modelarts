Switching the CUDA Version on the Terminal Page of a GPU-based Notebook Instance
================================================================================

For a GPU-based notebook instance, you can switch different versions of CUDA on the **Terminal** page of Jupyter.

CPU-based notebook instances do not use CUDA. Therefore, the following operations apply only to GPU-based notebook instances.

#. Create and open a notebook instance or open an existing notebook instance in the notebook instance list.

#. On the **Files** tab page of the Jupyter page, click **New** and select **Terminal**. The **Terminal** page is displayed.

#. Run the following command to go to **/usr/local**:

   .. code::

      cd /usr/local

#. For example, to switch to CUDA 10, run the following command:

   .. code::

      sudo ln -snf /usr/local/cuda-10.0 cuda

   | **Figure 1** Example of switching the CUDA version
   | |image1|


.. |image1| image:: /images/en-us_image_0000001156920929.png

