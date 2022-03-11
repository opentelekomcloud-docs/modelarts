Introduction to Model Templates
===============================

Because the configurations of models with the same functions are similar, ModelArts integrates the configurations of such models into a common template. By using this template, you can easily and quickly import models without compiling the **config.json** configuration file. In simple terms, a template integrates AI engine and model configurations. Each template corresponds to a specific AI engine and inference mode. With the templates, you can quickly import models to ModelArts.

Using a Template
----------------

The following uses the template described in `TensorFlow-py36 General Template <../model_templates/template_description/tensorflow-py36_general_template.html>`__ as an example. Upload the TensorFlow model package to OBS before using the template. Store the model files in the **model** directory. When creating a model using this template, you need to select the **model** directory.

#. On the **Import Model** page, set **Meta Model Source** to **Template**.

#. In the **Template** area, select **TensorFlow-py36 general template**.

   ModelArts also provides three filter criteria: **Type**, **Engine**, and **Environment**, helping you quickly find the desired template. If the three filter criteria cannot meet your requirements, you can enter keywords to search for the target template.

#. For **Model Folder**, select the **model** directory where the model files reside. For details, see `Template Description <../model_templates/index.html>`__.\ |image1|

   If a training job is executed for multiple times, different version directories are generated, such as V001 and V002, and the generated models are stored in the **model** folder in different version directories. When selecting model files, specify the **model** folder in the corresponding version directory.

#. If the default input and output mode of the selected template can be overwritten, you can select an input and output mode based on the model function or application scenario. **Input and Output Mode** is an abstract of the API in **config.json**. It describes the interface provided by the model for external inference. An input and output mode describes one or more APIs, and corresponds to a template.

   For details about the supported input and output modes, see `Input and Output Modes <../model_templates/index.html>`__.

Supported Templates
-------------------

-  `TensorFlow-py36 General Template <../model_templates/template_description/tensorflow-py36_general_template.html>`__
-  `MXNet-py36 General Template <../model_templates/template_description/mxnet-py36_general_template.html>`__
-  `PyTorch-py36 General Template <../model_templates/template_description/pytorch-py36_general_template.html>`__
-  `Caffe-CPU-py36 General Template <../model_templates/template_description/caffe-cpu-py36_general_template.html>`__
-  `Caffe-GPU-py36 General Template <../model_templates/template_description/caffe-gpu-py36_general_template.html>`__

Supported Input and Output Modes
--------------------------------

-  `Built-in Object Detection Mode <../model_templates/input_and_output_modes/built-in_object_detection_mode.html>`__
-  `Built-in Image Processing Mode <../model_templates/input_and_output_modes/built-in_image_processing_mode.html>`__
-  `Built-in Predictive Analytics Mode <../model_templates/input_and_output_modes/built-in_predictive_analytics_mode.html>`__
-  `Undefined Mode <../model_templates/input_and_output_modes/undefined_mode.html>`__



.. |image1| image:: /_static/images/note_3.0-en-us.png
