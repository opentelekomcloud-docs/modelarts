MXNet-py36 General Template
===========================

Introduction
------------

AI engine: MXNet 1.2.1; Environment: Python 3.6; Input and output mode: undefined mode. Select an appropriate input and output mode based on the model function or application scenario. When using the template to import a model, select the **model** directory containing the model files.

Template Input
--------------

The template input is the MXNet-based model package stored on OBS. Ensure that the OBS directory you use and ModelArts are in the same region. For details about model package requirements, see `Model Package Example <#model-package-example>`__.

Input and Output Mode
---------------------

`Undefined Mode <../../model_templates/input_and_output_modes/undefined_mode.html>`__ can be overwritten. That is, you can select another input and output mode during model creation.

Model Package Specifications
----------------------------

-  The model package must be stored in the OBS folder named **model**. Model files and the model inference code file are stored in the **model** folder.
-  The model inference code file is optional. If the file exists, the file name must be **customize_service.py**. Only one inference code file can exist in the **model** folder. For details about how to compile the model inference code file, see `Specifications for Compiling Model Inference Code <../../model_package_specifications/specifications_for_compiling_model_inference_code.html>`__.

-  The structure of the model package imported using the template is as follows:

   .. code-block::

      model/
      │
      ├── Model file                 //(Mandatory) The model file format varies according to the engine. For details, see the model package example.
      ├── Custom Python package           //(Optional) User's Python package, which can be directly referenced in the model inference code
      ├── customize_service.py  //(Optional) Model inference code file. The file name must be customize_service.py. Otherwise, the code is not considered as inference code.

Model Package Example
---------------------

**Structure of the MXNet-based model package**

When publishing the model, you only need to specify the **model** directory.

.. code-block::

   OBS bucket/directory name
   |── model    (Mandatory) The folder must be named model and is used to store model-related files.
       ├── <<Custom Python package>>       (Optional) User's Python package, which can be directly referenced in the model inference code
       ├── resnet-50-symbol.json    (Mandatory) Model definition file, which contains the neural network description of the model
       ├── resnet-50-0000.params    (Mandatory) Model variable parameter file, which contains parameter and weight information
       ├──customize_service.py      (Optional) Model inference code file. The file must be named customize_service.py. Only one inference code file exists. The .py file on which customize_service.py depends can be directly put in the model directory.


