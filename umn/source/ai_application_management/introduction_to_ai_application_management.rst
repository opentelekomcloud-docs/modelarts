:original_name: modelarts_23_0052.html

.. _modelarts_23_0052:

Introduction to AI Application Management
=========================================

AI development and optimization require frequent iterations and debugging. Changes in datasets, training code, or parameters affect the quality of models. If the metadata of the development process cannot be centrally managed, the optimal model may fail to be reproduced.

AI application management of ModelArts allows you to import all metamodels generated during training and centrally manage all iterated and debugged AI applications.

Usage Restrictions
------------------

-  In an ExeML project, after a model is deployed, the model is automatically uploaded to the AI application management list. However, AI applications generated by ExeML cannot be downloaded and can be used only for deployment and rollout.

Scenarios for Creating AI Applications
--------------------------------------

-  :ref:`Importing from Trained Models <modelarts_23_0054>`: You can create a training job on ModelArts and complete model training. After obtaining a satisfactory model, create an AI application for deployment.
-  :ref:`Importing from a Template <modelarts_23_0205>`: Because the configurations of models with the same functions are similar, ModelArts integrates the configurations of such models into a common template. By using this template, you can easily and quickly import models for creating AI applications without compiling the **config.json** configuration file.
-  :ref:`Importing from a Container Image <modelarts_23_0206>`: For AI engines that are not supported by ModelArts, you can import the models you compile to ModelArts using custom images and create AI applications for deployment.
-  :ref:`Importing from OBS <modelarts_23_0207>`: If you use a frequently-used framework to develop and train a model locally, you can import the model to ModelArts and create an AI application for deployment.

Functions of AI Application Management
--------------------------------------

.. table:: **Table 1** Functions of AI application management

   +-------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Supported Function                                          | Description                                                                                                                                                                   |
   +=============================================================+===============================================================================================================================================================================+
   | :ref:`Creating an AI Application <modelarts_23_0204>`       | Import the trained models to ModelArts and create AI applications for centralized management. The following provides the operation guide for each method of importing models. |
   |                                                             |                                                                                                                                                                               |
   |                                                             | -  :ref:`Importing a Meta Model from a Training Job <modelarts_23_0054>`                                                                                                      |
   |                                                             | -  :ref:`Importing a Meta Model from a Template <modelarts_23_0205>`                                                                                                          |
   |                                                             | -  :ref:`Importing a Meta Model from a Container Image <modelarts_23_0206>`                                                                                                   |
   |                                                             | -  :ref:`Importing a Meta Model from OBS <modelarts_23_0207>`                                                                                                                 |
   +-------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Managing AI Application Versions <modelarts_23_0055>` | To facilitate traceback and model tuning, ModelArts provides the AI application version management function. You can manage AI applications based on versions.                |
   +-------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
