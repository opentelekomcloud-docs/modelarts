:original_name: modelarts_05_3220.html

.. _modelarts_05_3220:

What Can I Do If a Notebook Instance Is Frequently Disconnected or Stuck After I Use MobaXterm to Connect to the Notebook Instance in SSH Mode?
===============================================================================================================================================

Symptom
-------

After MobaXterm is connected to a development environment, it is disconnected after a period of time.

Possible Cause
--------------

When MobaXterm is configured, **SSH keepalive** is not selected or **Stop server after** of MobaXterm Professional is set to a value that is too small.

Solution
--------

#. Open MobaXterm and click **Settings** on the menu bar.


   .. figure:: /_static/images/en-us_image_0000002079183505.png
      :alt: **Figure 1** Settings

      **Figure 1** Settings

#. On the MobaXterm configuration page, click the **SSH** tab and select **SSH keepalive**.


   .. figure:: /_static/images/en-us_image_0000002079183501.png
      :alt: **Figure 2** Selecting SSH keepalive

      **Figure 2** Selecting SSH keepalive

   .. note::

      If MobaXterm Professional is used, go to :ref:`step 3 <en-us_topic_0000002043025564__li20358102665416>`.

#. .. _en-us_topic_0000002043025564__li20358102665416:

   Change the default value **360 seconds** to **3600 seconds** or a larger value for **Stop server after**.


   .. figure:: /_static/images/en-us_image_0000002043025852.png
      :alt: **Figure 3** Setting Stop server after

      **Figure 3** Setting Stop server after
