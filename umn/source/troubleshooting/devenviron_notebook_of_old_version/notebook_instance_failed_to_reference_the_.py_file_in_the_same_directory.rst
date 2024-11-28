:original_name: modelarts_13_0003.html

.. _modelarts_13_0003:

Notebook Instance Failed to Reference the .py File in the Same Directory
========================================================================

Symptom
-------

After the user run the **python a.py** command in the **Terminal** environment of a notebook instance, the **.py** file in the same directory failed to be referenced, and the following error is reported:

ModuleNotFoundError: No module named 'b'.

:ref:`Figure 3 <en-us_topic_0000002079104157__fig441014137119>` shows the directory structure. :ref:`Figure 2 <en-us_topic_0000002079104157__fig784141118401>` provides details about the operation and the error.


.. figure:: /_static/images/en-us_image_0000002043025232.png
   :alt: **Figure 1** Directory structure

   **Figure 1** Directory structure

.. _en-us_topic_0000002079104157__fig784141118401:

.. figure:: /_static/images/en-us_image_0000002043183548.png
   :alt: **Figure 2** Reference error

   **Figure 2** Reference error

Possible Cause
--------------

After running the **ls** command in **Terminal** to check the file directory, it is found that **a.py** and **b.py** are not in the same directory.

.. _en-us_topic_0000002079104157__fig441014137119:

.. figure:: /_static/images/en-us_image_0000002079182877.png
   :alt: **Figure 3** Viewing the file directory

   **Figure 3** Viewing the file directory

Solution
--------

#. Log in to the ModelArts management console, and choose **DevEnviron > Notebooks**.

#. In the **Operation** column of the target notebook instance in the notebook list, click **Open** to go to the **Jupyter** page.

#. On the **Files** tab page of the **Jupyter** page, select the **a.py** and **b.py** files, and click **Sync OBS** to synchronize the selected objects from the OBS bucket path to the current container directory **~/work**. Then the objects can be invoked in code.


   .. figure:: /_static/images/en-us_image_0000002043025236.png
      :alt: **Figure 4** Synchronizing files

      **Figure 4** Synchronizing files
