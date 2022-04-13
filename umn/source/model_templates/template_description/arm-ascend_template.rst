.. _modelarts_23_0254:

Arm-Ascend Template
===================

Introduction
------------

AI engine: MindSpore; Environment: Python 3.5; Input and output mode: undefined mode. Select an appropriate input and output mode based on the model function or application scenario. When using the template to import a model, select the **model** directory containing the model files.

Template Input
--------------

The template input is the OM-based model package stored on OBS. Ensure that the OBS directory you use and ModelArts are in the same region. For details about model package requirements, see :ref:`Model Package Example <modelarts_23_0254__en-us_topic_0235925353_section1761262493211>`.

Input and Output Mode
---------------------

:ref:`Undefined Mode <modelarts_23_0103>` can be overwritten. That is, you cannot select another input and output mode during model creation.

Model Package Specifications
----------------------------

-  The model package must be stored in the OBS folder named **model**. Model files and the model inference code file are stored in the **model** folder.
-  The model inference code file is optional. If the file exists, the file name must be **customize_service.py**. Only one inference code file can exist in the **model** folder. For details about how to compile the model inference code file, see :ref:`Specifications for Compiling Model Inference Code <modelarts_23_0093>`.

-  The structure of the model package imported using the template is as follows:

   .. code-block::

      model/
      │
      ├── Model file                 //(Mandatory) The model file format varies according to the engine. For details, see the model package example.
      ├── Custom Python package           //(Optional) User's Python package, which can be directly referenced in the model inference code
      ├── customize_service.py  //(Optional) Model inference code file. The file name must be customize_service.py. Otherwise, the code is not considered as inference code.

.. _modelarts_23_0254__en-us_topic_0235925353_section1761262493211:

Model Package Example
---------------------

**Structure of the OM-based model package**

When publishing the model, you only need to specify the **model** directory.

.. code-block::

   OBS bucket/directory name
   |── model    (Mandatory) The folder must be named model and is used to store model-related files.
       ├── <<Custom Python package>>    (Optional) User's Python package, which can be directly referenced in the model inference code
       ├── model.om              (Mandatory) Protocol buffer file, which contains the diagram description of the model
       ├──customize_service.py   (Optional) Model inference code file. The file must be named customize_service.py. Only one inference code file exists. The .py file on which customize_service.py depends can be directly put in the model directory.
