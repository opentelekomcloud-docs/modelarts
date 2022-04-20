.. _modelarts_03_0143:

Basic Concepts
==============

-  Account

   An account is created upon successful registration with the cloud platform. The account has full access permissions for all of its cloud services and resources. It can be used to reset user passwords and grant user permissions.

-  Region

   A region is a physical location where a cloud service is deployed. Availability zones (AZ) in the same region can communicate with each other over an intranet but AZs in different regions cannot communicate with each other. By creating cloud resources in different regions, you can design applications to better meet customer requirements and comply with local laws and regulations.

-  AZ

   An AZ contains one or more physical data centers. It has independent cooling, fire extinguishing, moisture-proof, and electricity facilities. Within an AZ, computing, network, storage, and other resources are logically divided into multiple clusters. AZs within a region are interconnected using high-speed optical fibers to allow users to build cross-AZ high-availability systems.

-  Project

   Projects group and isolate compute, storage, and network resources across physical regions. A default project is provided for each region, and subprojects can be created under each default project. Users can be granted permissions to access all resources in a specific project. For more refined access control, create subprojects under a project and purchase resources in the subprojects. Users can then be assigned permissions to access only specific resources in the subprojects.

   .. _modelarts_03_0143__en-us_topic_0171316292_en-us_topic_0170640577_en-us_topic_0169294976_fig1189614168311:

   .. figure:: /_static/images/en-us_image_0171392261.gif
      :alt: **Figure 1** Project isolation model
   

      **Figure 1** Project isolation model
