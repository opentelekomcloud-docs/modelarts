:original_name: modelarts_trouble_0015.html

.. _modelarts_trouble_0015:

Error Message "No module named .*" Displayed in Training Job Logs
=================================================================

Perform the following operations to locate the fault:

#. :ref:`Checking Whether the Dependency Package Is Available <en-us_topic_0000002079104117__en-us_topic_0000001174943233_section9729952472>`
#. :ref:`Checking Whether the Dependency Package Path Can Be Detected <en-us_topic_0000002079104117__en-us_topic_0000001174943233_section11396125111268>`
#. :ref:`Checking Whether the Selected Resource Flavor Is Correct <en-us_topic_0000002079104117__section2182429896>`
#. :ref:`Summary and Suggestions <en-us_topic_0000002079104117__en-us_topic_0000001174943233_section169401039184514>`

.. _en-us_topic_0000002079104117__en-us_topic_0000001174943233_section9729952472:

Checking Whether the Dependency Package Is Available
----------------------------------------------------

If the dependency package is unavailable, use either of the following methods to install it:

-  Method 1 (recommended): When you create an algorithm, place the required file or installation package in the code directory.

   The required file varies depending on the dependency package type.

   -  **If the dependency package is an open-source installation package**

      Create a file named **pip-requirements.txt** in the code directory, and specify the dependency package name and version in the format of *Package name*\ **==**\ *Version* in the file.

      For example, the OBS path specified by **Code Directory** contains model files and the **pip-requirements.txt** file. The code directory structure is as follows:

      .. code-block::

         |---OBS path to the model boot file
              |---model.py               # Model boot file
              |---pip-requirements.txt   # Customized configuration file, which specifies the name and version of the dependency package

      The following shows the content of the **pip-requirements.txt** file:

      .. code-block::

         alembic==0.8.6
         bleach==1.4.3
         click==6.6

   -  **If the dependency package is a WHL package**

      If the training backend does not support the download of open-source installation packages or the use of custom WHL packages, the system cannot automatically download and install the package. In this case, place the WHL package in the code directory, create a file named **pip-requirements.txt**, and specify the name of the WHL package in the file. The dependency package must be in WHL format.

      For example, the OBS path specified by **Code Directory** contains model files, the WHL file, and the **pip-requirements.txt** file. The code directory structure is as follows:

      .. code-block::

         |---OBS path to the model boot file
              |---model.py               # Model boot file
              |---XXX.whl                # Dependency package. If multiple dependencies are required, place all of them here.
              |---pip-requirements.txt   # Customized configuration file, which specifies the name of the dependency package

      The following shows the content of the **pip-requirements.txt** file:

      .. code-block::

         numpy-1.15.4-cp36-cp36m-manylinux1_x86_64.whl
         tensorflow-1.8.0-cp36-cp36m-manylinux1_x86_64.whl

-  Method 2: Add the following code to the boot file to install the dependency package:

   .. code-block::

      import os
      os.system('pip install xxx')

In method 1, the dependency package can be downloaded and installed before the training job is started. In method 2, the dependency package is downloaded and installed during the running of the boot file.

.. _en-us_topic_0000002079104117__en-us_topic_0000001174943233_section11396125111268:

Checking Whether the Dependency Package Path Can Be Detected
------------------------------------------------------------

Before executing code locally, add **project_dir** to **PYTHONPATH** or install **project_dir** in **site-package**. ModelArts enables you to add **project_dir** to **sys.path** to resolve this issue.

Run **from module_dir import module_file** to import a package. The code structure is as follows:

.. code-block::

   project_dir
   |- main.py
   |- module_dir
   |  |- __init__.py
   |  |- module_file.py

.. _en-us_topic_0000002079104117__section2182429896:

Checking Whether the Selected Resource Flavor Is Correct
--------------------------------------------------------

Error message "No module named npu_bridge.npu_init" is displayed for a training job.

.. code-block::

   from npu_bridge.npu_init import *
   ImportError: No module named npu_bridge.npu_init

Check whether the flavor used by the training job supports NPUs. The possible cause is that the job selected a non-NPU flavor, for example, a GPU flavor. As a result, an error occurs when NPUs are used.

.. _en-us_topic_0000002079104117__en-us_topic_0000001174943233_section169401039184514:

Summary and Suggestions
-----------------------

Before creating a training job, use the ModelArts development environment to debug the training code to maximally eliminate errors in code migration.
