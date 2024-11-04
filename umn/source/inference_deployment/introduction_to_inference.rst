:original_name: inference-modelarts-0001.html

.. _inference-modelarts-0001:

Introduction to Inference
=========================

After an AI model is developed, you can use it to create an AI application and quickly deploy the application as an inference service. The AI inference capabilities can be integrated into your IT platform by calling APIs.


.. figure:: /_static/images/en-us_image_0000002043183192.png
   :alt: **Figure 1** Inference

   **Figure 1** Inference

-  Develop a model: Models can be developed in ModelArts or your local development environment. A locally developed model must be uploaded to OBS.
-  Create an AI application: Import the model file and inference file to the ModelArts model repository and manage them by version. Use these files to build an executable AI application.
-  Deploy as a service: Deploy the AI application as a container instance in the resource pool and register inference APIs that can be accessed externally.
-  Perform inference: Add the function of calling the inference APIs to your application to integrate AI inference into the service process.

.. _en-us_topic_0000002043024808__section5706068262:

Deploying an AI Application as a Service
----------------------------------------

After an AI application is created, you can deploy it as a service on the **Deploy** page. ModelArts supports the following deployment types:

-  :ref:`Real-time service <inference-modelarts-0018>`

   Deploy an AI application as a web service with real-time test UI and monitoring supported.

-  :ref:`Batch service <inference-modelarts-0040>`

   Deploy an AI application as a batch service that performs inference on batch data and automatically stops after data processing is complete.
