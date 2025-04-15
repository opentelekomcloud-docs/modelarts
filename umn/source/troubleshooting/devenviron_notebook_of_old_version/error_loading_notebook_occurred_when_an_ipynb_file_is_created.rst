:original_name: modelarts_13_0110.html

.. _modelarts_13_0110:

"Error loading notebook" Occurred When an IPYNB File Is Created
===============================================================

Symptom
-------

On the Notebook Jupyter page, "Error loading notebook" is displayed when an IPYNB file is created.


.. figure:: /_static/images/en-us_image_0000002268820217.png
   :alt: **Figure 1** Error message

   **Figure 1** Error message

Possible Causes
---------------

This issue may be caused by the attributes of the OBS bucket selected during the notebook instance creation. If the storage class of the OBS bucket is **Archive** and **Direct Reading** is disabled, this issue occurs.

Solution
--------

Log in to the OBS console, locate the OBS bucket of the notebook instance, and click the bucket name to go to the bucket details page. In the **Basic Configurations** area, locate the row of **Direct Reading**, click it, and select **Enable** in the dialog box that is displayed. After the configuration is complete, IPYNB files can be created on the notebook instance.
