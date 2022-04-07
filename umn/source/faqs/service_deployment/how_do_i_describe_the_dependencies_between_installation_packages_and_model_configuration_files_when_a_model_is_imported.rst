.. _modelarts_05_0161:

How Do I Describe the Dependencies Between Installation Packages and Model Configuration Files When a Model Is Imported?
========================================================================================================================

Symptom
-------

When importing a model from OBS or a container image, compile a model configuration file. The model configuration file describes the model usage, computing framework, precision, inference code dependency package, and model API. The configuration file must be in JSON format. In the configuration file, **dependencies** indicates the packages that the model inference code depends on. Model developers need to provide the package name, installation mode, and version constraints. For details about the parameters, see . The dependency structure array needs to be set for the **dependencies** parameter.

Solution
--------

When the installation package has dependency relationships, the **dependencies** parameter in the model configuration file supports multiple **dependency** structure arrays, which are entered in list format.

The dependencies in list format must be installed in sequence. For example, install **Cython**, **pytest-runner**, and **pytest** before installing **mmcv-full**. When entering the installation packages in list format in the configuration file, write **Cython**, **pytest-runner**, and **pytest** in front of the **mmcv-full** structure array.

Example:

.. code-block::

   "dependencies": [
       {
       "installer": "pip",
       "packages": [
           {
               "package_name": "Cython"
           },
           {
               "package_name": "pytest-runner"
           },
           {
               "package_name": "pytest"
           }]
       },

       {
       "installer": "pip",
       "packages": [
           {
               "restraint": "ATLEAST",
               "package_version": "5.0.0",
               "package_name": "Pillow"
           },
           {
               "restraint": "ATLEAST",
               "package_version": "1.4.0",
               "package_name": "torch"
           },
           {
               "restraint": "ATLEAST",
               "package_version": "1.19.1",
               "package_name": "numpy"
           },
           {
               "restraint": "ATLEAST",
               "package_version": "1.2.0",
               "package_name": "mmcv-full"
           }]
       }
   ]
