.. _modelarts_21_0001:

Introduction to ExeML
=====================

ExeML
-----

ModelArts ExeML is a customized code-free model development tool that helps users start AI application development from scratch with high flexibility. ExeML automates model design, parameter tuning and training, and model compression and deployment with the labeled data. Developers do not need to develop basic and encoding capabilities, but only to upload data and complete model training and deployment as prompted by ExeML.

Currently, you can use ExeML to quickly create image classification, and object detection models. It can be widely used in industrial, retail, and security fields.

-  Image classification classifies and identifies objects in images.
-  Object detection identifies the position and class of each object in images.

ExeML Usage Process
-------------------

With ModelArts ExeML, you can develop AI models without coding. You only need to upload data, create a project, label the data, publish training, and deploy the trained model. Up to 100 ExeML projects can be created. For details, see :ref:`Figure 1 <modelarts_21_0001__en-us_topic_0284258830_en-us_topic_0169445434_fig3917183328>`.

.. _modelarts_21_0001__en-us_topic_0284258830_en-us_topic_0169445434_fig3917183328:

.. figure:: /_static/images/en-us_image_0000001110921482.png
   :alt: **Figure 1** Usage process of ExeML


   **Figure 1** Usage process of ExeML

ExeML Projects
--------------

-  **Image Classification**

   An image classification project aims to classify images. You only need to add images and label the images. After the images are labeled, an image classification model can be quickly generated. It can automatically classify offerings, vehicle types, and defective goods. For example, in the quality check scenario, you can upload a product image, label the image as qualified or unqualified, and train and deploy a model to inspect product quality.

-  **Object Detection**

   An object detection project aims to identify the class and location of objects in images. You only need to add images and label objects in the images with proper bounding boxes. The labled images will be used as the training set for creating a model. The model can identify multiple objects and count the number of objects in a single image, as well as inspect employees' dress code and perform unattended inspection of article placement.
