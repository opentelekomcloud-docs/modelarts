:original_name: modelarts_23_0098.html

.. _modelarts_23_0098:

Introduction to Model Templates
===============================

Because the configurations of models with the same functions are similar, ModelArts integrates the configurations of such models into a common template. By using this template, you can easily and quickly import models and create AI applications without compiling the **config.json** configuration file. In simple terms, a template integrates AI engine and model configurations. Each template corresponds to a specific AI engine and inference mode. With the templates, you can quickly import models to ModelArts and create AI applications.

Using a Template
----------------

Upload the model package to OBS before using the template. Store the model files in the **model** directory. When creating an AI application using this template, you need to select the **model** directory. For details, see :ref:`Importing a Meta Model from a Template <modelarts_23_0205>`.

#. On the **Create** page, set **Meta Model Source** to **Template**.

#. In the **Model Template** area, select a common template.

   ModelArts also provides three filter criteria: **Type**, **Engine**, and **Environment**, helping you quickly find the desired template. If the three filter criteria cannot meet your requirements, you can enter keywords to search for the target template.


   .. figure:: /_static/images/en-us_image_0000001806111326.png
      :alt: **Figure 1** Selecting a template

      **Figure 1** Selecting a template

#. For **Model Folder**, select the **model** directory where the model files reside. For details, see :ref:`Templates <modelarts_23_0118>`.

   .. note::

      If a training job is executed for multiple times, different version directories are generated, such as V001 and V002, and the generated models are stored in the **model** folder in different version directories. When selecting model files, specify the **model** folder in the corresponding version directory.

#. If the default input and output mode of the selected template can be overwritten, you can select an input and output mode based on the model function or application scenario. **Input and Output Mode** is an abstract of the API in **config.json**. It describes the interface provided by the model for external inference. An input and output mode describes one or more APIs, and corresponds to a template.

   For details about the supported input and output modes, see :ref:`Input and Output Modes <modelarts_23_0099>`.
