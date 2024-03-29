:original_name: modelarts_21_0034.html

.. _modelarts_21_0034:

Where Are Models Generated by ExeML Stored? What Other Operations Are Supported?
================================================================================

Unified Model Management
------------------------

For an ExeML project, after the model training is complete, the generated model is automatically displayed on the **Model Management > Models** page. The model name is automatically generated by the system. Its prefix is the same as the name of the ExeML project for easy identification.

.. caution::

   Models generated by ExeML cannot be downloaded.


.. figure:: /_static/images/en-us_image_0000001404825686.png
   :alt: **Figure 1** Models generated by ExeML

   **Figure 1** Models generated by ExeML

What Other Operations Are Supported for Models Generated by ExeML?
------------------------------------------------------------------

-  **Deploying models as real-time and batch services**

   On the **ExeML** page, models can only be deployed as real-time services. You can deploy models as batch services on the **Model Management > Models** page.

   It should be noted that resources with other specifications, such as dedicated resource pools and GPU resources, can be used when you create a model deployment task on the **Model Management > Models** page. On the ExeML project page, only **ExeML (CPU)** can be used to deploy models.

-  **Creating a version**

   When creating a new version, you can select a meta model only from a ModelArts training job, OBS, model template, or custom image. You cannot create a version from the original ExeML project.

-  **Deleting a model or its version**
