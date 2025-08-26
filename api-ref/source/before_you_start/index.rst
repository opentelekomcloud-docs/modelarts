:original_name: modelarts_03_0139.html

.. _modelarts_03_0139:

Before You Start
================

ModelArts is a one-stop AI development platform geared toward developers and data scientists of all skill levels. It enables you to rapidly build, train, and deploy models anywhere (from the cloud to the edge), and manage full-lifecycle AI workflows. ModelArts accelerates AI development and fosters AI innovation with key capabilities, including data preprocessing and auto labeling, distributed training, automated model building, and one-click workflow execution. You can use ModelArts through open APIs.

ModelArts supports Representational State Transfer (REST) APIs, allowing you to call APIs using HTTPS. For details about API calling, see :ref:`Calling APIs <modelarts_03_0005>`.

.. _en-us_topic_0000002374896637__section2081352311426:

Endpoint
--------

An endpoint is the request address for calling an API. Endpoints vary depending on services and regions. To obtain the regions and endpoints, contact the enterprise administrator.

A service endpoint consists of the service name, region ID, and external domain name in the format of "{service_name}.{region_id}.{external_domain_name}". :ref:`Table 1 <en-us_topic_0000002374896637__en-us_topic_0000001072357044_table24011519165716>` describes these parameters.

.. _en-us_topic_0000002374896637__en-us_topic_0000001072357044_table24011519165716:

.. table:: **Table 1** Endpoint parameters

   +----------------------+----------------------------------------------+---------------------------------------------+
   | Parameter            | Description                                  | How to Obtain                               |
   +======================+==============================================+=============================================+
   | service_name         | Service name abbreviation (case-insensitive) | **modelarts** for ModelArts by default.     |
   +----------------------+----------------------------------------------+---------------------------------------------+
   | region_id            | Region ID                                    | Contact the system administrator to obtain. |
   +----------------------+----------------------------------------------+---------------------------------------------+
   | external_domain_name | External domain name suffix                  | Contact the system administrator to obtain. |
   +----------------------+----------------------------------------------+---------------------------------------------+

.. important::

   If an endpoint uses a domain name, configure the hosts file in the format of "{float-ip} {service_name}.{region_id}.{external_domain_name}" on the local PC. Contact the system administrator to obtain **float-ip**.

Constraints
-----------

-  For more constraints, see API description.

Basic Concepts
--------------

-  Account

   An account is created upon successful registration with the cloud platform. The account has full access permissions for all of its cloud services and resources. It can be used to reset user passwords and grant user permissions.

-  Region

   A region is a geographic area where cloud resources are deployed. Availability zones (AZs) in the same region can communicate with each other over an intranet, while AZs in different regions are isolated from each other. Deploying cloud resources in different regions can better suit certain user requirements or comply with local laws or regulations.

-  AZ

   An AZ contains one or more physical data centers. Each AZ has independent cooling, fire extinguishing, moisture-proof, and electricity facilities. An AZ's computing, network, storage, and other resources are logically divided into multiple clusters. AZs within a region are interconnected using high-speed optical fibers to allow users to build cross-AZ high-availability systems.

-  Project

   Projects group and isolate compute, storage, and network resources across physical regions. A default project is provided for each region, and subprojects can be created under each default project. Users can be granted permissions to access all resources in a specific project. If you need more refined access control, create subprojects under a default project and create resources in subprojects. Then you can assign users the permissions required to access only the resources in the specific subprojects.


   .. figure:: /_static/images/en-us_image_0000002351870506.png
      :alt: **Figure 1** Project isolation model

      **Figure 1** Project isolation model

-  :ref:`Overview <modelarts_03_0001>`
-  :ref:`Endpoint <modelarts_03_0141>`
-  :ref:`Constraints <modelarts_03_0142>`
-  :ref:`Basic Concepts <modelarts_03_0143>`

.. toctree::
   :maxdepth: 1
   :hidden: 

   overview
   endpoint
   constraints
   basic_concepts
