.. _modelarts_23_0098:

Introduction to Model Templates
===============================

Because the configurations of models with the same functions are similar, ModelArts integrates the configurations of such models into a common template. By using this template, you can easily and quickly import models without compiling the **config.json** configuration file. In simple terms, a template integrates AI engine and model configurations. Each template corresponds to a specific AI engine and inference mode. With the templates, you can quickly import models to ModelArts.

Using a Template
----------------

The following uses the template described in :ref:`TensorFlow-py36 General Template <modelarts_23_0162>` as an example. Upload the TensorFlow model package to OBS before using the template. Store the model files in the **model** directory. When creating a model using this template, you need to select the **model** directory.

#. On the **Import Model** page, set **Meta Model Source** to **Template**.

#. In the **Template** area, select **TensorFlow-py36 general template**.

   ModelArts also provides three filter criteria: **Type**, **Engine**, and **Environment**, helping you quickly find the desired template. If the three filter criteria cannot meet your requirements, you can enter keywords to search for the target template.

#. For **Model Folder**, select the **model** directory where the model files reside. For details, see :ref:`Template Description <modelarts_23_0118>`.

   .. note::

      If a training job is executed for multiple times, different version directories are generated, such as V001 and V002, and the generated models are stored in the **model** folder in different version directories. When selecting model files, specify the **model** folder in the corresponding version directory.

#. If the default input and output mode of the selected template can be overwritten, you can select an input and output mode based on the model function or application scenario. **Input and Output Mode** is an abstract of the API in **config.json**. It describes the interface provided by the model for external inference. An input and output mode describes one or more APIs, and corresponds to a template.

   For details about the supported input and output modes, see :ref:`Input and Output Modes <modelarts_23_0099>`.

.. _modelarts_23_0098__en-us_topic_0172873520_section44801025155417:

Supported Templates
-------------------

-  :ref:`TensorFlow-py36 General Template <modelarts_23_0162>`
-  :ref:`MXNet-py36 General Template <modelarts_23_0164>`
-  :ref:`PyTorch-py36 General Template <modelarts_23_0166>`
-  :ref:`Caffe-CPU-py36 General Template <modelarts_23_0169>`
-  :ref:`Caffe-GPU-py36 General Template <modelarts_23_0170>`

.. _modelarts_23_0098__en-us_topic_0172873520_section737759781:

Supported Input and Output Modes
--------------------------------

-  :ref:`Built-in Object Detection Mode <modelarts_23_0100>`
-  :ref:`Built-in Image Processing Mode <modelarts_23_0101>`
-  :ref:`Built-in Predictive Analytics Mode <modelarts_23_0102>`
-  :ref:`Undefined Mode <modelarts_23_0103>`
