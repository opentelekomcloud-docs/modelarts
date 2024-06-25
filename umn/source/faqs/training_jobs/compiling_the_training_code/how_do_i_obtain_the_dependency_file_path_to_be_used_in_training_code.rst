:original_name: modelarts_05_0280.html

.. _modelarts_05_0280:

How Do I Obtain the Dependency File Path to be Used in Training Code?
=====================================================================

Since locally developed code must be uploaded to the ModelArts backend, you may set an invalid dependency file path. A recommended general solution to this problem is that you to use the OS API to obtain the absolute path of the dependency files.

The following shows an example of obtaining the path of dependency files in other folders using the OS API.

File directory structure:

.. code-block::

   project_root                   #Root directory of code
    └─bootfile.py               #Boot file
    └─otherfileDirectory        #Directory of dependency files
          └─otherfile.py        #Dependency files

Add the following code to the boot file to obtain the path (**otherfile_path**) of dependency files:

.. code-block::

   import os
   current_path = os.path.dirname(os.path.realpath(__file__)) # Obtain the path of the boot file bootfile.py.
   project_root = os.path.dirname(current_path) # Obtain the root directory of the project using the path of the boot file, which is the code directory set on ModelArts console.
   otherfile_path = os.path.join(project_root, "otherfileDirectory", "otherfile.py")  # Obtain the path of the dependency files using the root directory of the project.
