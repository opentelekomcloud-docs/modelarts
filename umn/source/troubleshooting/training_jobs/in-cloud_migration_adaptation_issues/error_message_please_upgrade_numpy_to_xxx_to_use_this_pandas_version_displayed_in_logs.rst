:original_name: modelarts_trouble_0052.html

.. _modelarts_trouble_0052:

Error Message "Please upgrade numpy to >= xxx to use this pandas version" Displayed in Logs
===========================================================================================

Symptom
-------

Dependency conflicts occur when other packages are installed. There are special requirements on the NumPy library. However, NumPy cannot be uninstalled. The error message similar to the following is displayed:

.. code-block::

   your numpy version is 1.14.5.Please upgrade numpy to >= 1.15.4 to use this pandas version

Possible Causes
---------------

Both Conda and pip packages are installed. Some packages cannot be uninstalled.

Solution
--------

Perform the following operations to resolve this issue:

#. Uninstall the components that can be uninstalled in NumPy.

#. Delete the NumPy folder in the **site-packages** directory.

#. Install the required version again.

   .. code-block::

      import os
      os.system("pip uninstall -y numpy")
      os.system('rm -rf /home/work/anaconda/lib/python3.6/site-packages/numpy/')
      os.system("pip install numpy==1.15.4")

Summary and Suggestions
-----------------------

Before creating a training job, use the ModelArts development environment to debug the training code to maximally eliminate errors in code migration.
