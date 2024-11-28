:original_name: modelarts_13_0008.html

.. _modelarts_13_0008:

Error Occurs When Using a Notebook Instance to Run Code, Indicating That No File Is Found in /tmp
=================================================================================================

Symptom
-------

When the a notebook instance is used to run code, the following error occurs:

.. code-block::

   FileNotFoundError: [Error 2] No usable temporary directory found in ['/tmp', '/var/tmp', '/usr/tmp', 'home/ma-user/work/SR/RDN_train_base']


.. figure:: /_static/images/en-us_image_0000002079182933.png
   :alt: **Figure 1** Code running error

   **Figure 1** Code running error

Possible Cause
--------------

Check whether a large amount of data is saved in **/tmp**.

Solution
--------

#. Go to the **Terminal** page. In the **/tmp** directory, run the **du -sh \*** command to check the space usage of the directory.

   .. code-block::

      sh-4.3$cd /tmp
      sh-4.3$du -sh *
      4.0K    core-js-banners
      0       npm-19-41ed4c62
      6.7M    v8-compile-cache-1000

#. Delete unnecessary large files.

   a. Delete the sample file **test.txt**: **rm -f /home/ma-user/work/data/test.txt**
   b. Delete the sample folder **data**: **rm -rf /home/ma-user/work/data/**
