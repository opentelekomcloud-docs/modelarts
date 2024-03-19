:original_name: modelarts_23_0169.html

.. _modelarts_23_0169:

Caffe-CPU-py37 General Template
===============================

Introduction
------------

AI engine: CPU-based Caffe 1.0; Environment: Python 3.7; Input and output mode: undefined mode. Select an appropriate input and output mode based on the model function or application scenario. When using the template to import a model, select the **model** directory containing the model files.

Template Input
--------------

The template input is the Caffe-based model package stored on OBS. Ensure that the OBS directory you use and ModelArts are in the same region. For details about model package requirements, see :ref:`Model Package Example <modelarts_23_0169__en-us_topic_0000001255997612_en-us_topic_0193596270_section164016197320>`.

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

.. _modelarts_23_0169__en-us_topic_0000001255997612_en-us_topic_0193596270_section164016197320:

Model Package Example
---------------------

**Structure of the Caffe-based model package**

When publishing the model, you only need to specify the **model** directory.

.. code-block::

   OBS bucket/directory name
   |── model    (Mandatory) The folder must be named model and is used to store model-related files.
       |── <<Custom Python package>>      (Optional) User's Python package, which can be directly referenced in model inference code
       |── deploy.prototxt         (Mandatory) Caffe model file, which contains information such as the model network structure
       |── resnet.caffemodel       (Mandatory) Caffe model file, which contains variable and weight information
      |── customize_service.py    (Optional) Model inference code file. The file must be named customize_service.py. Only one inference code file exists. The .py file on which customize_service.py depends can be directly put in the model directory.
