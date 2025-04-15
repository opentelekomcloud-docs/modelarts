:original_name: modelarts_13_0006.html

.. _modelarts_13_0006:

Disk Space Used Up
==================

Symptom
-------

-  Error message "No Space left on Device" is displayed when a notebook instance is used.

-  Error message "Disk quota exceeded" is displayed when code is executed in a notebook instance.

   |image1|

Possible Causes
---------------

-  After a file is deleted from the navigation pane on the left of JupyterLab, the file is moved to the recycle bin by default. This occupies memory, leading to insufficient disk space.
-  The disk quota is insufficient.

Solution
--------

Check the storage space used by the VM, check the memory used by files in the recycle bin, and delete unnecessary large files from the recycle bin.

#. On the notebook instance details page, view the storage capacity of the instance.

#. Check the storage space used by the VM. The storage space is typically close to the storage capacity.

   .. code-block:: text

      cd /home/ma-user/work
      du -h --max-depth 0

   |image2|

#. Run the following commands to check the memory used by the recycle bin (recycle bin files are stored in **/home/ma-user/work/.Trash-1000/files** by default):

   .. code-block:: text

      cd /home/ma-user/work/.Trash-1000/
      du -ah

   |image3|

#. Delete unnecessary large files from the recycle bin. Deleted files cannot be restored.

   .. code-block:: text

      rm {File path}

   |image4|

   .. note::

      If the name of the folder or file you want to delete contains spaces, add single quotation marks to the name.

      |image5|

#. Run the following commands to check the storage space used by the VM again:

   .. code-block:: text

      cd /home/ma-user/work
      du -h --max-depth 0

#. If the notebook instance uses an EVS disk for storage, expand the storage capacity on the notebook instance details page.

Summary and Suggestions
-----------------------

It is a good practice to delete unnecessary files when using a notebook instance to prevent a training failure caused by insufficient disk space.

.. |image1| image:: /_static/images/en-us_image_0000002233739992.png
.. |image2| image:: /_static/images/en-us_image_0000002268819201.png
.. |image3| image:: /_static/images/en-us_image_0000002268739305.png
.. |image4| image:: /_static/images/en-us_image_0000002233899828.png
.. |image5| image:: /_static/images/en-us_image_0000002268739289.png
