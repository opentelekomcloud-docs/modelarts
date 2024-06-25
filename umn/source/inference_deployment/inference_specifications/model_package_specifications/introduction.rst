:original_name: inference-modelarts-0055.html

.. _inference-modelarts-0055:

Introduction
============

When creating an AI application on the AI application management page, make sure that any meta model imported from OBS complies with certain specifications.

.. note::

   -  The model package specifications are used when you import one model. If you import multiple models, for example, there are multiple model files, use custom images.
   -  If you want to use an AI engine that is not supported by ModelArts, use a custom image.
   -  To create a custom image, refer to :ref:`Custom Image Specifications for Creating an AI Application <modelarts_23_0219>`
   -  For more examples of custom scripts, see :ref:`Examples of Custom Scripts <inference-modelarts-0078>`.

The model package must contain the **model** directory. The **model** directory stores the model file, model configuration file, and model inference code file.

-  **Model files:** The requirements for model files vary according to the model package structure. For details, see :ref:`Model Package Example <en-us_topic_0000001943974161__en-us_topic_0172466148_section828936173917>`.
-  **Model configuration file**: The model configuration file must be available and its name is consistently to be **config.json**. There must be only one model configuration file. For details about how to edit a model configuration file, see :ref:`Specifications for Editing a Model Configuration File <inference-modelarts-0056>`.
-  **Model inference code file**: It is mandatory. The file name is consistently to be **customize_service.py**. There must be only one model inference code file. For details about how to edit model inference code, see :ref:`Specifications for Writing Model Inference Code <inference-modelarts-0057>`.

   -  The .py file on which **customize_service.py** depends can be directly stored in the **model** directory. Use relative import for the custom package.
   -  The other files on which **customize_service.py** depends can be stored in the **model** directory. Only absolute paths can be used to access these files. For details, see :ref:`Obtaining an Absolute Path <en-us_topic_0000001910014882__en-us_topic_0172466150_li135956421288>`.

ModelArts also provides custom script examples of common AI engines. For details, see :ref:`Examples of Custom Scripts <inference-modelarts-0079>`.

.. _en-us_topic_0000001943974161__en-us_topic_0172466148_section828936173917:

Model Package Example
---------------------

-  Structure of the TensorFlow-based model package

   When publishing the model, you only need to specify the **ocr** directory.

   .. code-block::

      OBS bucket/directory name
      |── ocr
      |   ├── model (Mandatory) Name of a fixed subdirectory, which is used to store model-related files
      |   │   ├── <<Custom Python package>> (Optional) Your Python package, which can be directly referenced in model inference code
      |   │   ├── saved_model.pb (Mandatory) Protocol buffer file, which contains the diagram description of the model
      |   │   ├── variables Name of a fixed sub-directory, which contains the weight and deviation rate of the model. It is mandatory for the main file of a *.pb model.
      |   │   │   ├── variables.index Mandatory
      |   │   │   ├── variables.data-00000-of-00001 Mandatory
      |   │   ├──config.json (Mandatory) Model configuration file. The file name is fixed to config.json. Only one model configuration file is allowed.
      |   │   ├──customize_service.py (Mandatory) Model inference code. The file name is fixed to customize_service.py. Only one model inference code file exists. The files on which customize_service.py depends can be directly stored in the model directory.

-  Structure of the MindSpore-based model package

   .. code-block::

      OBS bucket/directory name
      |── resnet
      |   ├── model (Mandatory) Name of a fixed subdirectory, which is used to store model-related files
      |   │   ├── <<Custom Python package>> (Optional) Your Python package, which can be directly referenced in model inference code
      |   │   ├── checkpoint_lenet_1-1_1875.ckpt (Mandatory) Model file in ckpt format trained using MindSpore
      |   │   ├── config.json (Mandatory) Model configuration file. The file name is fixed to config.json. Only one model configuration file is allowed.
      |   │   ├── customize_service.py (Mandatory) Model inference code. The file name is fixed to customize_service.py. Only one model inference code file exists. The files on which customize_service.py depends can be directly stored in the model directory.
      |   │   ├── tmp.om (Mandatory) An empty .om file that enables the model package to be imported

-  Structure of the image-based model package

   When publishing the model, you only need to specify the **resnet** directory.

   .. code-block::

      OBS bucket/directory name
      |── resnet
      |   ├── model (Mandatory) Name of a fixed subdirectory, which is used to store model-related files
      |   │  ├──config.json (Mandatory) Model configuration file (the address of the SWR image must be configured). The file name is fixed to config.json. Only one model configuration file is allowed.

-  Structure of the PyTorch-based model package

   When publishing the model, you only need to specify the **resnet** directory.

   .. code-block::

      OBS bucket/directory name
      |── resnet
      |   ├── model (Mandatory) Name of a fixed subdirectory, which is used to store model-related files
      |   │  ├── <<Custom Python package>> (Optional) Your Python package, which can be directly referenced in model inference code
      |   │  ├── resnet50.pth (Mandatory) PyTorch model file, which contains variable and weight information and is saved as state_dict
      |   │  ├──config.json (Mandatory) Model configuration file. The file name is fixed to config.json. Only one model configuration file is allowed.
      |   │  ├──customize_service.py (Mandatory) Model inference code. The file name is fixed to customize_service.py. Only one model inference code file exists. The files on which customize_service.py depends can be directly stored in the model directory.
