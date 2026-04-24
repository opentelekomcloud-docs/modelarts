:original_name: modelarts_05_3180.html

.. _modelarts_05_3180:

Failed to Use a Purchased Dedicated Resource Pool to Create New-Version Notebook Instances
==========================================================================================

Symptom
-------

A dedicated resource pool that has been purchased cannot be selected for creating a notebook instance, resulting in the creation failure.

A message is displayed, indicating that the development environment has not been initialized in the dedicated resource pool.

Possible Causes
---------------

A newly purchased dedicated resource pool can be used to create notebook instances only after its development environment is initialized.

Solution
--------

Initialize the development environment on the dedicated resource pool page.

#. Go to the **Resource Management > Elastic Clusters** page and choose **More** > **Set Job Type** in the **Operation** column.


   .. figure:: /_static/images/en-us_image_0000002578546691.png
      :alt: **Figure 1** Set Job Type

      **Figure 1** Set Job Type

#. In the **Set Job Type** dialog box, select **DevEnviron** and click **OK**. Then, the development environment is being initialized. After its status changes to **Running**, the newly purchased dedicated resource pool can be used to create notebook instances.


   .. figure:: /_static/images/en-us_image_0000002548110696.png
      :alt: **Figure 2** Setting job type to DevEnviron

      **Figure 2** Setting job type to DevEnviron


   .. figure:: /_static/images/en-us_image_0000002571423233.png
      :alt: **Figure 3** Initializing the development environment

      **Figure 3** Initializing the development environment
