:original_name: modelarts_30_0040.html

.. _modelarts_30_0040:

Dynamically Expanding EVS Disk Capacity
=======================================

Overview
--------

If a notebook instance uses an EVS disk for storage, the disk is mounted to **/home/ma-user/work/** of the notebook container and the disk capacity can be expanded by up to 200 GB when the instance is running.

Application Scenarios
---------------------

During notebook development, select a small EVS disk capacity, for example, 5 GB, when creating a notebook instance because the storage requirements are low at the initial stage. After the development, a large volume of data must be trained. Then, expand the disk capacity to cost-effectively meet your service needs.

Restrictions
------------

-  The target notebook instance must use EVS for storage.
-  Up to 100 GB can be expanded at a time. Additionally, the total capacity after expansion cannot exceed 4096 GB.
-  If the original capacity of an EVS disk is 4096 GB, the disk capacity cannot be expanded.
-  After the instance is stopped, the expanded capacity still takes effect.

Procedure
---------

#. Log in to the ModelArts management console. In the left navigation pane, choose **DevEnviron > Notebook** to switch to the new-version **Notebook** page.

#. Click the name of a running notebook instance. On the instance details page, click **Expansion**.


   .. figure:: /_static/images/en-us_image_0000001853037265.png
      :alt: **Figure 1** Instance details page

      **Figure 1** Instance details page

#. Set the capacity to be expanded and click **OK**. **Expanding** shows that the capacity expansion is in progress. After the expansion, the displayed storage capacity is the expanded capacity.
