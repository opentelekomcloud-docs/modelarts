.. _modelarts_23_0091:

Model Package Specifications
============================

When you import models in **Model Management**, if the meta model is imported from OBS or a container image, the model package must meet the following specifications:

-  The model package must contain the **model** directory. The **model** directory stores the model file, model configuration file, and model inference code.
-  The model configuration file must exist and its name is fixed to **config.json**. There exists only one model configuration file. For details about how to compile the model configuration file, see :ref:`Specifications for Compiling the Model Configuration File <modelarts_23_0092>`.
-  The model inference code file is optional. If this file is required, the file name is fixed to **customize_service.py**. There must be one and only one such file. For details about how to compile the model inference code, see :ref:`Specifications for Compiling Model Inference Code <modelarts_23_0093>`.

   .. note::

      -  The **.py** file on which **customize_service.py** depends can be directly stored in the **model** directory. Use the Python import mode to import the custom package.
      -  The other files on which **customize_service.py** depends can be stored in the **model** directory. You must use absolute paths to access these files. For more details, see :ref:`Obtaining an Absolute Path <modelarts_23_0093__en-us_topic_0172466150_li135956421288>`.

ModelArts also provides custom script examples of common AI engines. For details, see :ref:`Examples of Custom Scripts <modelarts_23_0173>`.

Model Package Example
---------------------

-  Structure of the TensorFlow-based model package

   When publishing the model, you only need to specify the **ocr** directory.

   .. code-block::

      OBS bucket/directory name
      |── ocr
      |   ├── model (Mandatory) Name of a fixed subdirectory, which is used to store model-related files
      |   │   ├── <<Custom Python package>> (Optional) User's Python package, which can be directly referenced in the model inference code
      |   │   ├── saved_model.pb (Mandatory) Protocol buffer file, which contains the diagram description of the model
      |   │   ├── variables Name of a fixed sub-directory, which contains the weight and deviation rate of the model. It is mandatory for the main file of the *.pb model.
      |   │   │   ├── variables.index Mandatory
      |   │   │   ├── variables.data-00000-of-00001 Mandatory
      |   │   ├──config.json (Mandatory) Model configuration file. The file name is fixed to config.json. Only one model configuration file is supported.
      |   │   ├──customize_service.py (Optional) Model inference code. The file name is fixed to customize_service.py. Only one model inference code file exists. The files on which customize_service.py depends can be directly stored in the model directory.

-  Structure of the MindSpore-based model package

   .. code-block::

      OBS bucket/directory name
      |── resnet
      |   ├── model (Mandatory) Name of a fixed subdirectory, which is used to store model-related files
      |   │   ├── <<Custom Python package>> (Optional) User's Python package, which can be directly referenced in the model inference code
      |   │   ├── checkpoint_lenet_1-1_1875.ckpt (Mandatory) Model file in ckpt format trained using MindSpore
      |   │   ├──config.json (Mandatory) Model configuration file. The file name is fixed to config.json. Only one model configuration file is supported.
      |   │   ├──customize_service.py (Optional) Model inference code. The file name is fixed to customize_service.py. Only one model inference code file is supported. The files on which customize_service.py depends can be directly stored in the model directory.

-  Structure of the MXNet-based model package

   When publishing the model, you only need to specify the **resnet** directory.

   .. code-block::

      OBS bucket/directory name
      |── resnet
      |   ├── model (Mandatory) Name of a fixed subdirectory, which is used to store model-related files
      |   │   ├── <<Custom Python package>> (Optional) User's Python package, which can be directly referenced in the model inference code
      |   │   ├── resnet-50-symbol.json (Mandatory) Model definition file, which contains the neural network description of the model
      |   │   ├── resnet-50-0000.params (Mandatory) Model variable parameter file, which contains parameter and weight information
      |   │   ├──config.json (Mandatory) Model configuration file. The file name is fixed to config.json. Only one model configuration file is supported.
      |   │   ├──customize_service.py (Optional) Model inference code. The file name is fixed to customize_service.py. Only one model inference code file exists. The files on which customize_service.py depends can be directly stored in the model directory.

-  Structure of the Image-based model package

   When publishing the model, you only need to specify the **resnet** directory.

   .. code-block::

      OBS bucket/directory name
      |── resnet
      |   ├── model (Mandatory) Name of a fixed subdirectory, which is used to store model-related files
      |   │  ├──config.json (Mandatory) Model configuration file (the address of the SWR image must be configured). The file name is fixed to config.json. Only one model configuration file is supported.

-  Structure of the PySpark-based model package

   When publishing the model, you only need to specify the **resnet** directory.

   .. code-block::

      OBS bucket/directory name
      |── resnet
      |   ├── model (Mandatory) Name of a fixed subdirectory, which is used to store model-related files
      |   │  ├── <<Custom Python package>> (Optional) User's Python package, which can be directly referenced in the model inference code
      |   │  ├── spark_model (Mandatory) Model directory, which contains the model content saved by PySpark
      |   │  ├──config.json (Mandatory) Model configuration file. The file name is fixed to config.json. Only one model configuration file is supported.
      |   │  ├──customize_service.py (Optional) Model inference code. The file name is fixed to customize_service.py. Only one model inference code file exists. The files on which customize_service.py depends can be directly stored in the model directory.

-  Structure of the PyTorch-based model package

   When publishing the model, you only need to specify the **resnet** directory.

   .. code-block::

      OBS bucket/directory name
      |── resnet
      |   ├── model (Mandatory) Name of a fixed subdirectory, which is used to store model-related files
      |   │  ├── <<Custom Python package>> (Optional) User's Python package, which can be directly referenced in the model inference code
      |   │  ├── resnet50.pth (Mandatory) PyTorch model file, which contains variable and weight information and is saved as state_dict
      |   │  ├──config.json (Mandatory) Model configuration file. The file name is fixed to config.json. Only one model configuration file is supported.
      |   │  ├──customize_service.py (Optional) Model inference code. The file name is fixed to customize_service.py. Only one model inference code file exists. The files on which customize_service.py depends can be directly stored in the model directory.

-  Structure of the Caffe-based model package

   When publishing the model, you only need to specify the **resnet** directory.

   .. code-block::

      OBS bucket/directory name
      |── resnet
      |   |── model (Mandatory) Name of a fixed subdirectory, which is used to store model-related files
      |   |   |── <<Custom Python package>> (Optional) User's Python package, which can be directly referenced in the model inference code
      |   |   |── deploy.prototxt (Mandatory) Caffe model file, which contains information such as the model network structure
      |   |   |── resnet.caffemodel (Mandatory) Caffe model file, which contains variable and weight information
      |   |   |── config.json (Mandatory) Model configuration file. The file name is fixed to config.json. Only one model configuration file is supported.
      |   |   |── customize_service.py  (Optional) Model inference code. The file name is fixed to customize_service.py. Only one model inference code file exists. The files on which customize_service.py depends can be directly stored in the model directory. 

-  Structure of the XGBoost-based model package

   When publishing the model, you only need to specify the **resnet** directory.

   .. code-block::

      OBS bucket/directory name
      |── resnet
      |   |── model (Mandatory) Name of a fixed subdirectory, which is used to store model-related files
      |   |   |── <<Custom Python package>> (Optional) User's Python package, which can be directly referenced in the model inference code
      |   |   |── *.m (Mandatory): Model file whose extension name is .m
      |   |   |── config.json (Mandatory) Model configuration file. The file name is fixed to config.json. Only one model configuration file is supported.
      |   |   |── customize_service.py  (Optional) Model inference code. The file name is fixed to customize_service.py. Only one model inference code file exists. The files on which customize_service.py depends can be directly stored in the model directory. 

-  Structure of the Scikit_Learn-based model package

   When publishing the model, you only need to specify the **resnet** directory.

   .. code-block::

      OBS bucket/directory name
      |── resnet
      |   |── model (Mandatory) Name of a fixed subdirectory, which is used to store model-related files
      |   |   |── <<Custom Python package>> (Optional) User's Python package, which can be directly referenced in the model inference code
      |   |   |── *.m (Mandatory): Model file whose extension name is .m
      |   |   |── config.json (Mandatory) Model configuration file. The file name is fixed to config.json. Only one model configuration file is supported.
      |   |   |── customize_service.py  (Optional) Model inference code. The file name is fixed to customize_service.py. Only one model inference code file exists. The files on which customize_service.py depends can be directly stored in the model directory. 
