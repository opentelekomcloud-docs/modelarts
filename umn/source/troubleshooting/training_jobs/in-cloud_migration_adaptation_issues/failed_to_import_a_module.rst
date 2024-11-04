:original_name: modelarts_13_0014.html

.. _modelarts_13_0014:

Failed to Import a Module
=========================

Symptom
-------

The following error occurs in the log when a module is imported to a ModelArts training job:

.. code-block::

   Traceback (most recent call last):File "project_dir/main.py", line 1, in <module>from module_dir import module_file

.. code-block::

   ImportError: No module named module_dir

.. code-block::

   ImportError: No module named xxx

.. _en-us_topic_0000002043025112__section1237061220324:

Possible Cause
--------------

-  When a training job is imported to the module, the previous two error messages are displayed in the log. The possible causes are as follows:

   Before running code locally, you need to add **project_dir** to **PYTHONPATH** or install **project_dir** in **site-package**. However, on ModelArts, you can add **project_dir** to **sys.path** to solve this problem.

   Use **from module_dir import module_file** to import a package. The code structure is as follows:

   .. code-block::

      project_dir
      |- main.py
      |- module_dir
      |  |- __init__.py
      |  |- module_file.py

-  When a training job is imported to the module, the error message **"ImportError: No module named xxx"** is displayed in the log. It can be determined that the environment does not contain the Python package on which the user depends.

Solution
--------

-  When a training job is imported to the module, the previous two error messages are displayed in the log. The solution is as follows:

   #. Ensure that the imported module contains **\__init__.py** used for creating **module_dir**. :ref:`Possible Cause <en-us_topic_0000002043025112__section1237061220324>` provides the code structure.

   #. Because the location of **project_dir** in the container is unknown, use an absolute path by adding **project_dir** to **sys.path** in file **main.py**, and import the following information:

      .. code-block::

         import os
         import sys
         # __file__ is the absolute path of the main.py script.
         # os.path.dirname(__file__) is the parent directory of main.py, that is, the absolute path of project_dir.
         current_path = os.path.dirname(__file__)
         sys.path.append(current_path)
         # Import other modules after sys.path.append is executed.
         from module_dir import module_file

-  When a training job is imported to the module, the error message **"ImportError: No module named xxx"** is displayed in the log. Add the following code to install the dependency package:

   .. code-block::

      import os
      os.system('pip install xxx')
