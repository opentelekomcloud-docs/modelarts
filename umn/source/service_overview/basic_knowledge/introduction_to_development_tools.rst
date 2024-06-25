:original_name: modelarts_01_0028.html

.. _modelarts_01_0028:

Introduction to Development Tools
=================================

.. note::

   This document describes the DevEnviron notebook functions of the new version.

Software development is a process of reducing developer costs and improving development experience. In AI development, ModelArts is dedicated to improving AI development experience and simplifying the development process. ModelArts DevEnviron uses cloud native resources and integrates the development tool chain to provide better in-cloud AI development experience for AI development, exploration, and teaching.

ModelArts notebook for seamless in-cloud and on-premises collaboration

-  In-cloud JupyterLab, local IDE, and ModelArts plug-ins for remote development and debugging, tailored to your needs
-  In-cloud development environment with AI compute resources, cloud storage, and built-in AI engines
-  Custom runtime environment saved as an image for training and inference

Feature 1: Remote development, allowing remote access to notebook from a local IDE
----------------------------------------------------------------------------------

The notebook of the new version provides remote development. After enabling remote SSH, you can remotely access the ModelArts notebook development environment to debug and run code from a local IDE.

Due to limited local resources, developers using a local IDE run and debug code typically on a CPU or GPU server shared between team members. Building and maintaining the CPU or GPU server are costly.

ModelArts notebook instances are out of the box with various built-in engines and flavors for you to select. You can use a dedicated container environment. Only after simple configurations, you can remotely access the environment to run and debug code from your local IDE.

ModelArts notebook can be regarded as an extension of a local development environment. The operations such as data reading, training, and file saving are the same as those performed in a local environment.

ModelArts notebook allows you to use in-cloud resources while with local coding habits unchanged.

A local IDE supports Visual Studio (VS) Code, PyCharm, and SSH. In addition, the PyCharm Toolkit plug-ins allow you to easily use cloud resources.

Feature 2: Preset images that are out-of-the-box with optimized configurations and supporting mainstream AI engines
-------------------------------------------------------------------------------------------------------------------

The AI engines and versions preset in each image are fixed. When creating a notebook instance, specify an AI engine and version, including the chip type.

ModelArts DevEnviron provides a group of preset images, including PyTorch, TensorFlow, and MindSpore images. You can use a preset image to start your notebook instance. After the development in the instance, submit a training job without any adaptation.

The image versions preset in ModelArts are determined based on user feedback and version stability. If your development can be carried out using the versions preset in ModelArts, for example, MindSpore 1.5, use preset images. These images have been fully verified and have many commonly-used installation packages built in. They are out-of-the-box, relieving you from configuring the environment.

The images preset in ModelArts DevEnviron include:

-  Common preset packages: common AI engines such as PyTorch and MindSpore based on standard Conda, common data analysis software packages such as Pandas and Numpy, and common tool software such as CUDA and CUDNN, meeting common AI development requirements.

-  Preset Conda environments: A Conda environment and basic Conda Python (excluding any AI engine) are created for each preset image. The following figure shows the Conda environment for the preset MindSpore.

   |image1|

   Select a Conda environment based on whether the AI engine is used for debugging.

-  Notebook: a web application that enables you to code on the GUI and combine the code, mathematical equations, and visualized content into a document.

-  JupyterLab plug-ins: enable flavor changing and instance stopping to improving user experience.

-  Remote SSH: allows you to remotely debug a notebook instance from a local PC.

.. note::

   -  To simplify operations, ModelArts notebook of the new version does not support switchover between AI engines in a notebook instance.
   -  AI engines vary based on regions. For details about the AI engines available in a region, see the AI engines displayed on the management console.

Feature 3: JupyterLab, an online interactive development and debugging tool
---------------------------------------------------------------------------

ModelArts integrates open-source JupyterLab for online interactive development and debugging. You can use the notebook on the ModelArts management console to compile and debug code and train models based on the code, without concerning environment installation or configuration.

JupyterLab is an interactive development environment. It is the next-generation product of Jupyter Notebook. JupyterLab enables you to compile notebooks, operate terminals, edit Markdown text, enable interaction, and view CSV files and images.

.. |image1| image:: /_static/images/en-us_image_0000001910019930.png
