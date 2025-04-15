:original_name: modelarts_21_0001.html

.. _modelarts_21_0001:

Introduction to ExeML
=====================

ExeML
-----

ModelArts ExeML is a customized code-free model development tool that helps you start codeless model development with high flexibility. ExeML automates model design, parameter tuning and training, and model compression and deployment based on the labeled data. With ExeML, you only need to upload data and perform simple operations as prompted on the ExeML GUI to train and deploy models. Up to 100 ExeML projects can be created.

You can use ExeML to quickly build models for image classification, and object detection. ExeML is widely used in industrial, retail, and security sectors.

-  Image classification: identifies a class of objects in images.
-  Object detection: identifies the position and class of each object in an image.

ExeML Process
-------------

With ModelArts ExeML, you can develop AI models without coding. You only need to upload data, create a project, label the data, publish training, and deploy the trained model. Up to 100 ExeML projects can be created. For details, see :ref:`Figure 1 <en-us_topic_0000002233744696__en-us_topic_0000001799497412_en-us_topic_0284258830_en-us_topic_0169445434_fig3917183328>`.

.. _en-us_topic_0000002233744696__en-us_topic_0000001799497412_en-us_topic_0284258830_en-us_topic_0169445434_fig3917183328:

.. figure:: /_static/images/en-us_image_0000002233744880.png
   :alt: **Figure 1** ExeML process

   **Figure 1** ExeML process

ExeML Projects
--------------

-  **Image Classification**

   An image classification project aims to classify images. You only need to add images and label them. Then, an image classification model can be quickly generated for automatically classifying offerings, vehicle types, and defective goods. For example, in the quality check scenario, you can upload a product image, label the image as qualified or unqualified, and train and deploy a model to inspect product quality.

-  **Object Detection**

   An object detection project aims to identify the class and location of objects in images. You only need to add images and label objects in the images with proper bounding boxes. The labeled images will be used as a training set for building a model to identify multiple objects or provide the number of objects in a single image. Object detection can also be used to inspect employees' dress code and perform unattended inspection of article placement.

Model Deployment Specifications
-------------------------------

Different types of ExeML projects support different specifications for model deployment. For details, see :ref:`Table 1 <en-us_topic_0000002233744696__en-us_topic_0000001799497412_en-us_topic_0284258830_en-us_topic_0169445434_en-us_topic_0284258830_en-us_topic_0169445434_table4446919194615>`.

.. _en-us_topic_0000002233744696__en-us_topic_0000001799497412_en-us_topic_0284258830_en-us_topic_0169445434_en-us_topic_0284258830_en-us_topic_0169445434_table4446919194615:

.. table:: **Table 1** Available deployment specifications for different types of projects

   +-----------------------------------+-------------------------------------------+
   | Type                              | Available Model Deployment Specifications |
   +===================================+===========================================+
   | Image classification              | Compute-intensive 3 instance (CPU)        |
   |                                   |                                           |
   |                                   | Compute-intensive 2 instance (GPU)        |
   +-----------------------------------+-------------------------------------------+
   | Object detection                  | Compute-intensive 3 instance (CPU)        |
   |                                   |                                           |
   |                                   | Compute-intensive 2 instance (GPU)        |
   +-----------------------------------+-------------------------------------------+
