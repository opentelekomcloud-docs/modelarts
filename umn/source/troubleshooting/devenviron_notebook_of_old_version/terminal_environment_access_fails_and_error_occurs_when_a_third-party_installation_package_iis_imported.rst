:original_name: modelarts_13_0002.html

.. _modelarts_13_0002:

**Terminal** Environment Access Fails and Error Occurs When a Third-party Installation Package Iis Imported
===========================================================================================================

Symptom
-------

-  The environment failed to be accessed after the user runs the **source activate xxx** command in **Terminal**.
-  The basic framework package or the package installed by running the **pip install** command cannot be imported to a notebook instance.
-  The following error is displayed when you import a package to a notebook instance: **ImportError: No module named XXX**. As a result, the package cannot be used.

Possible Cause
--------------

Based on the preceding symptoms, the cause is that the Terminal environment is inactivated.

Solution
--------

#. Log in to the ModelArts management console, and choose **DevEnviron > Notebooks**.

#. In the **Operation** column of the target notebook instance in the notebook list, click **Open** to go to the **Jupyter** page.

#. On the **Files** tab page of the **Jupyter** page, click **New** and select **Terminal**. The **Terminal** page is displayed.


   .. figure:: /_static/images/en-us_image_0000001910009168.png
      :alt: **Figure 1** Going to the **Terminal** page

      **Figure 1** Going to the **Terminal** page

#. Run the following command to obtain the command line for activating the environment, as shown in :ref:`Figure 2 <en-us_topic_0000001910008648__fig9291155351810>`.

   .. code-block::

      cat /home/ma-user/README

   For example, to activate **TensorFlow-1.8**, run the following command to access the TensorFlow-1.8 environment and start development:

   .. code-block::

      source /home/ma-user/anaconda3/bin/activate TensorFlow-1.8

   .. _en-us_topic_0000001910008648__fig9291155351810:

   .. figure:: /_static/images/en-us_image_0000001909849160.png
      :alt: **Figure 2** Activating the Terminal environment

      **Figure 2** Activating the Terminal environment
