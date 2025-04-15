:original_name: modelarts_13_0246.html

.. _modelarts_13_0246:

What Do I Do If No Kernel Is Displayed After a Notebook File Is Created?
========================================================================

Symptom
-------

After a notebook file is created, "No Kernel" is displayed in the upper right corner of the page.

|image1|

Possible Causes
---------------

The **code.py** file in the work directory conflicts with the name of the import code file on which the kernel depends.

Solution
--------

#. View the latest log file starting with **kernelgateway** in **/home/ma-user/log/** and search for the logs near **Starting kernel**. If the stack similar to the following is displayed, the possible cause is that the name of the **code.py** file in the work directory conflicts with the name of the import code file on which the kernel depends.

   |image2|

#. To resolve this issue, rename the **code.py** file in the work directory.

   **code.py** and **select.py** are typically prone to conflict.

.. |image1| image:: /_static/images/en-us_image_0000002268819313.jpg
.. |image2| image:: /_static/images/en-us_image_0000002233740092.jpg
