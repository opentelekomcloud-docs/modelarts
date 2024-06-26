:original_name: modelarts_23_0262.html

.. _modelarts_23_0262:

TensorFlow-py36 General Template
================================

Introduction
------------

AI engine: TensorFlow 1.8; Environment: Python 3.6; Input and output mode: Undefined. Select an appropriate input and output mode based on the model function or application scenario. When using the template to import a model, select the **model** directory containing the model files.

Template Input
--------------

The template input is the TensorFlow-based model package stored on OBS. Ensure that the OBS directory you use and ModelArts are in the same region. For details about model package requirements, see :ref:`Model Package Example <modelarts_23_0262__en-us_topic_0000001251827549_en-us_topic_0193596262_section1761262493211>`.

Input and Output Mode
---------------------

:ref:`Undefined Mode <modelarts_23_0103>` can be overwritten. You can select another input and output mode during model creation.

Model Package Specifications
----------------------------

-  The model package must be stored in the OBS folder named **model**. Model files and the model inference code file are stored in the **model** folder.
-  The model inference code file is optional, but if there is one, it must be named **customize_service.py**. There can only be one such file in the **model** folder. For details about how to write model inference code, see :ref:`Specifications for Writing Model Inference Code <modelarts_23_0093>`.

-  The structure of the model package imported using the template is as follows:

   .. code-block::

      model/
      │
      ├── Model file                 //(Mandatory) The model file format varies depending on the engine. For details, see the model package example.
      ├── Custom Python package           //(Optional) Your Python package, which can be directly referenced in model inference code
      ├── customize_service.py  //(Optional) Model inference code file. The file name must be customize_service.py, otherwise it will not be recognized.

.. _modelarts_23_0262__en-us_topic_0000001251827549_en-us_topic_0193596262_section1761262493211:

Model Package Example
---------------------

**Structure of the TensorFlow-based model package**

When publishing the model, you only need to specify the **model** directory.

.. code-block::

   OBS bucket/directory name
   |── model    (Mandatory) The folder must be named model and is used to store model-related files.
       ├── <<Custom Python package>>    (Optional) Your Python package, which can be directly referenced in model inference code
       ├── saved_model.pb        (Mandatory) Protocol buffer file, which contains the diagram description of the model
       ├── variables             Mandatory for the main file of the *.pb model. The folder must be named variables and contains the weight deviation of the model.
           ├── variables.index                   Mandatory
           ├── variables.data-00000-of-00001     Mandatory
       ├──customize_service.py   (Optional) Model inference code file. The file must be named customize_service.py. Only one inference code file exists. The .py file on which customize_service.py depends can be directly put in the model directory.
