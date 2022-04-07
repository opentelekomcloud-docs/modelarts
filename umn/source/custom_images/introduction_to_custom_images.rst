.. _modelarts_23_0084:

Introduction to Custom Images
=============================

ModelArts provides multiple frequently-used built-in engines. However, when users have special requirements for the deep learning engine and development library, the built-in AI engines cannot meet user requirements. ModelArts provides the custom image function to allow users to customize engines.

The bottom layer of ModelArts uses the container technology. Custom images refer to that users create container images and run them on ModelArts. The custom image function supports command line parameters and environment variables in free-text format. The custom images are highly flexible and support the job boot requirements of any computing engine.

The following services are also required for creating a custom image: Software Repository for Container (SWR), OBS, and Elastic Cloud Server (ECS)

Application Scenarios of Custom Images
--------------------------------------

-  **For Training Models**

   If you have developed a model or training script locally and the AI engine you use is not supported by ModelArts, you can create a custom image based on the basic image packages provided by ModelArts and upload the custom image to SWR. Then, you can use the custom image to create a training job on ModelArts and use the resources provided by ModelArts to train models.

-  **For Importing Models**

   If you use an AI engine that is not supported by ModelArts to develop a model, you can create a custom image, import the image to ModelArts for unified management, and deploy the model as a service.
