:original_name: modelarts_05_0097.html

.. _modelarts_05_0097:

Why Can't I Use os.system ('cd xxx') to Access the Corresponding Folder During Job Training?
============================================================================================

If you cannot access the corresponding folder by using **os.system('cd xxx')** in the boot script of the training job, you are advised to use the following method:

.. code-block::

   import os
   os.chdir('/home/work/user-job-dir/xxx')
