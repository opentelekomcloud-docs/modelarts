:original_name: resmgmt-modelarts_0063.html

.. _resmgmt-modelarts_0063:

Using TMS Tags to Manage Resources by Group
===========================================

ModelArts can work with Tag Management Service (TMS). When creating resource-consuming tasks in ModelArts, configure tags for these tasks so that ModelArts can use tags to manage resources by group.

ModelArts allows you to configure tags when you create training jobs, notebook instances, real-time inference services, or standard dedicated resource pools.

Operation Process
-----------------

#. :ref:`Step 1 Create Predefined Tags on TMS <en-us_topic_0000002459970966__section147721921112>`
#. :ref:`Step 2 Add a Tag to a ModelArts Task <en-us_topic_0000002459970966__section4865163351118>`
#. :ref:`Step 3 Obtain ModelArts Resource Usage by Resource Type in TMS <en-us_topic_0000002459970966__section13310346154612>`

.. _en-us_topic_0000002459970966__section147721921112:

Step 1 Create Predefined Tags on TMS
------------------------------------

Log in to the TMS console and create tags on the **Predefined Tags** page. The created tags are global and can be used in all regions.

.. _en-us_topic_0000002459970966__section4865163351118:

Step 2 Add a Tag to a ModelArts Task
------------------------------------

When creating a notebook instance, training job, or real-time inference services in ModelArts, configure a tag for the task.

-  Add a tag to a ModelArts notebook instance.

   Add a tag when you create a notebook instance. Alternatively, after creating a notebook instance, add a tag on the **Tags** tab on the instance details page.

-  Add a tag to a ModelArts training job.

   Add a tag when you create a training job. Alternatively, after creating a training job, add a tag on the **Tags** tab on the job details page.

-  Add a tag to a ModelArts real-time service.

   Add a tag when you create a real-time service. Alternatively, after creating a real-time service, add a tag on the **Tags** tab on the service details page.

-  Add a tag to a ModelArts dedicated resource pool.

   Add a tag when you create a standard dedicated resource pool. Alternatively, after creating a dedicated resource pool, add a tag in the **Tags** tab on the resource pool details page.

.. note::

   When adding a tag to a ModelArts task, you can create new tags by specifying the keys and values of the new tags. The created tags are available for only the current project.

.. _en-us_topic_0000002459970966__section13310346154612:

Step 3 Obtain ModelArts Resource Usage by Resource Type in TMS
--------------------------------------------------------------

Log in to the TMS console. On the **Resources Tag** page, view resource tasks in specified regions based on resource types and tags.

-  **Region**: A region and availability zone (AZ) identify the location of a data center. You can create resources in a specific region and AZ. For details about regions, see `Region and AZ <https://docs.otc.t-systems.com/image-management-service/umn/overview/basic_concepts/region_and_az.html>`__.
-  **Resource Type**: :ref:`Table 1 <en-us_topic_0000002459970966__table51761326797>` lists the resource types that can be viewed on ModelArts.
-  **Resource Tag**: If no tag is specified, all resources are displayed, regardless of whether the resources are configured with tags. One or multiple tags can be selected to obtain resource usage.

.. _en-us_topic_0000002459970966__table51761326797:

.. table:: **Table 1** Resource types that can be viewed on ModelArts

   ========================= ==========================================
   Resource Type             Description
   ========================= ==========================================
   ModelArts-Notebook        Notebook instances in ModelArts DevEnviron
   ModelArts-TrainingJob     ModelArts training jobs
   ModelArts-RealtimeService ModelArts real-time inference services
   ModelArts-ResourcePool    ModelArts dedicated resource pools
   ========================= ==========================================

.. note::

   If your organization has configured tag policies for ModelArts, add tags to resources based on the policies. If a tag does not comply with the tag policies, resource creation may fail. Contact your organization administrator to learn more about tag policies.
