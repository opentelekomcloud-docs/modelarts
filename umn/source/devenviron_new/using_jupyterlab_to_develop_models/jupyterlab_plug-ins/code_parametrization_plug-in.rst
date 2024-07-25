:original_name: devtool-modelarts_0212.html

.. _devtool-modelarts_0212:

Code Parametrization Plug-in
============================

Use Guide
---------

-  The **Add Form** and **Edit Form** buttons are available only to the shortcut menu of code cells.


   .. figure:: /_static/images/en-us_image_0000001846137413.png
      :alt: **Figure 1** Viewing a code cell

      **Figure 1** Viewing a code cell

-  After opening new code, add a form before editing it.


   .. figure:: /_static/images/en-us_image_0000001799498236.png
      :alt: **Figure 2** Shortcut menu of code cells

      **Figure 2** Shortcut menu of code cells

Add Form
--------

If you click **Add Form**, a code cell will be split into the code and form edit area. Click **Edit** on the right of the form to change the default title.


.. figure:: /_static/images/en-us_image_0000001846057345.png
   :alt: **Figure 3** Two edit areas

   **Figure 3** Two edit areas

Edit Form
---------

If you click **Edit Form**, four sub-options will be displayed: **Add new form field**, **Hide code**, **Hide form**, and **Show All**.

-  You can set the form field type to **dropdown**, **input**, and **slider**. See :ref:`Figure 4 <en-us_topic_0000001846056313__en-us_topic_0000001278648233_fig86841216610>`. Each time a field is added, the corresponding variable is added to the code and form areas. If a value in the form area is changed, the corresponding variable in the code area is also changed.

   .. note::

      When creating a dropdown form, click **ADD Item** and add at least two items. See :ref:`Figure 5 <en-us_topic_0000001846056313__en-us_topic_0000001278648233_fig946213314619>`.

   .. _en-us_topic_0000001846056313__en-us_topic_0000001278648233_fig86841216610:

   .. figure:: /_static/images/en-us_image_0000001799498252.png
      :alt: **Figure 4** Form style of dropdown, input, and slider

      **Figure 4** Form style of dropdown, input, and slider

   .. _en-us_topic_0000001846056313__en-us_topic_0000001278648233_fig946213314619:

   .. figure:: /_static/images/en-us_image_0000001846057329.png
      :alt: **Figure 5** Creating a dropdown form

      **Figure 5** Creating a dropdown form


   .. figure:: /_static/images/en-us_image_0000001846137397.png
      :alt: **Figure 6** Deleting a form

      **Figure 6** Deleting a form

   -  If the form field type is set to **dropdown**, the supported variable types are **raw** and **string**.\ |image1|
   -  If the form field type is set to **input**, the supported variable types are **boolean**, **date**, **integer**, **number**, **raw**, and **string**.
   -  If the form field type is set to **slider**, the minimum value, maximum value, and step can be set.

-  If you click **Hide code**, the code area will be hidden.

-  If you click **Hide form**, the form area will be hidden.

-  If you click **Show All**, both the code and form areas will be displayed.

.. |image1| image:: /_static/images/en-us_image_0000001846058197.png
