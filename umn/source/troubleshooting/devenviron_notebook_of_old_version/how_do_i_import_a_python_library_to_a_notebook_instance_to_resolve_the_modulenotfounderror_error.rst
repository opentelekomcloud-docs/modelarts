:original_name: modelarts_13_0104.html

.. _modelarts_13_0104:

How Do I Import a Python Library to a Notebook Instance to Resolve the ModuleNotFoundError Error?
=================================================================================================

Importing the Python Library to a Notebook Instance with EVS Disks Attached
---------------------------------------------------------------------------

#. Obtain the address of the Python library to be imported, and follow the instructions in **Adding Folders to sys.path** of Python 3 to import the Python library. There are two methods to import the Python library. The widely used method is to use the **PYTHONPATH** environment variable.
#. After the Python library is imported, you can view your **PYTHONPATH** in the notebook instance.

   a. View the **PYTHONPATH** in **IPYNB**. Run the following command in the code input box to view the **PYTHONPATH**. If the returned address is the same as the address of the Python library that you set, the Python library has been imported.

      **!echo $PYTHONPATH**

   b. View the **PYTHONPATH** on the **Terminal** page. Run the following command to view the **PYTHONPATH**. If the returned address is the same as the address of the Python library that you set, the Python library has been imported.

      **echo $PYTHONPATH**

Importing the Python Library to a Notebook Instance with OBS Storage
--------------------------------------------------------------------

The methods of importing the Python library vary according to the size of the python library file.

#. If the size of the python library file is less than 100 MB, use either of the following methods:

   -  Upload the Python files to OBS, and synchronize the Python files from OBS to the notebook instance . Follow the instructions in Adding Folders to sys.path of Python 3 to import the Python library. Use the **PYTHONPATH** environment variable to import the library.
   -  Upload the Python files to OBS, and synchronize the Python files from OBS to the notebook instance using . Follow the instructions in "Adding Folders to sys.path" of Python 3 to import the Python library. It is a good practice to use the **PYTHONPATH** environment variable to import the library.

#. If the size of the Python library file is greater than 100 MB, use the following method:

   Upload the Python files to OBS, and synchronize the Python files from OBS to the notebook instance using MoXing, and then MoXing can use the OBS files. Follow the instructions in Adding Folders to sys.path of Python 3 to import the Python library. Use the **PYTHONPATH** environment variable to import the library.

After the Python library is imported, you can view your **PYTHONPATH** in the notebook instance.

#. View the **PYTHONPATH** in **IPYNB**. Run the following command in the code input box to view the **PYTHONPATH**. If the returned address is the same as the address of the Python library that you set, the Python library has been imported.

   **!echo $PYTHONPATH**

#. View the **PYTHONPATH** on the **Terminal** page. Run the following command to view the **PYTHONPATH**. If the returned address is the same as the address of the Python library that you set, the Python library has been imported.

   **echo $PYTHONPATH**
