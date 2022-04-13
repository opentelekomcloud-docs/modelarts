.. _modelarts_05_0063:

How Do I Create a Training Job When a Dependency Package Is Referenced in a Model?
==================================================================================

When a model references a dependency package, select a frequently-used framework to create training jobs. In addition, place the required file or installation package in the code directory. The requirements vary based on the dependency package that you use.

-  **Open-source installation package**

   .. note::

      It is not allowed to install the package using the GitHub source code.

   Create a file named **pip-requirements.txt** in the code directory. In this file, specify the name and version of the dependency package in the format of *Package name*\ **==**\ *Version*.

   For example, the OBS path specified by **Code Directory** contains model files and the **pip-requirements.txt** file. The following shows the code directory structure:

   .. code-block::

      |---OBS path to the model boot file
           |---model.py               #Model boot file
           |---pip-requirements.txt   #Customized configuration file, which specifies the name and version of the dependency package

   The following shows the content of the **pip-requirements.txt** file:

   .. code-block::

      alembic==0.8.6
      bleach==1.4.3
      click==6.6

-  **Customized WHL file**

   When you use a customized .whl file, the system cannot automatically download and install the file. Place the .whl file in the code directory, create a file named **pip-requirements.txt**, and specify the name of the .whl file in the created file. The dependency package must be a .whl file.

   For example, the OBS path specified by **Code Directory** contains model files, .whl file, and **pip-requirements.txt** file. The following shows the code directory structure:

   .. code-block::

      |---OBS path to the model boot file
           |---model.py               #Model boot file
           |---XXX.whl                #Dependency package. If multiple dependencies are required, place all of them here.
           |---pip-requirements.txt   #Customized configuration file, which specifies the name of the dependency package

   The following shows the content of the **pip-requirements.txt** file:

   .. code-block::

      numpy-1.15.4-cp36-cp36m-manylinux1_x86_64.whl
      tensorflow-1.8.0-cp36-cp36m-manylinux1_x86_64.whl
