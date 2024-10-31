:original_name: modelarts_24_0078.html

.. _modelarts_24_0078:

Basic Concepts
==============

ModelArts allows you to configure fine-grained permissions for refined management of resources and permissions. This is commonly used by large enterprises, but it is complex for individual users. It is recommended that individual users configure permissions for using ModelArts by referring to :ref:`Assigning Permissions to Individual Users for Using ModelArts <modelarts_24_0085>`.

.. note::

   **Do I need to read this document?**

   Read this document if any of the following description matches your situation.

   -  You are an enterprise user, and

      -  There are multiple departments in your enterprise, and you need to control users' permissions so that users in different departments can access only their dedicated resources and functions.
      -  There are multiple roles (such as administrators, algorithm developers, and application O&M personnel) in your enterprise. You need them to use only specific functions.
      -  There are logically multiple environments (such as the development environment, pre-production environment, and production environment) and are isolated from each other. You need to control users' permissions on different environments.
      -  You need to control permissions of specific IAM user or user group.

   -  You are an individual user, and you have created multiple IAM users. You need to assign different ModelArts permissions to different IAM users.
   -  You need to understand the concepts and operations of ModelArts permissions management.

ModelArts uses Identity and Access Management (IAM) for most permissions management functions. Before reading below, learn about *Basic Concepts*. This helps you better understand this document.

To implement fine-grained permissions management, ModelArts provides permission control, agency authorization, and workspace. The following describes the details.

ModelArts Permissions and Agencies
----------------------------------

Exposed ModelArts functions are controlled through IAM permissions. For example, if you as an IAM user need to create a training job on ModelArts, you must have the **modelarts:trainJob:create** permission. For details about how to assign permissions to a user (you need to add the user to a user group and then assign permissions to the user group), see *Permissions Management*.

ModelArts must access other services for AI computing. For example, ModelArts must access OBS to read your data for training. In such cases, ModelArts accesses other cloud services as users. To ensure security, ModelArts requires your authorization before accessing any cloud services, which is the process of agency. Then, you can perform AI computing tasks on ModelArts.

The following summarizes permissions management:

-  Your access to any cloud service is controlled through IAM. You must have the permissions of the cloud service. (The required service permissions vary depending on the functions you use.)
-  To use ModelArts functions, you need to grant permissions through IAM.
-  ModelArts must be authorized by you to access other cloud services for AI computing.

ModelArts Permissions Management
--------------------------------

By default, new IAM users do not have any permissions assigned. You need to add a user to one or more groups, and assign permissions policies or roles to these groups. Users inherit permissions of the groups to which they are added. This process is called authorization. After authorization, users can perform operations on ModelArts based on permissions.

.. caution::

   ModelArts is a project-level service deployed and accessed in specific physical regions. When you authorize an agency, you can set the scope for the permissions you select to all resources, enterprises projects, or region-specific projects. If you specify region-specific projects, the selected permissions will be applied to resources in these projects.

   ModelArts supports enterprise projects. You can specify an enterprise project when selecting the authorization scope.

|image1|

When assigning permissions to a user group, IAM does not directly assign specific permissions to the user group. Instead, IAM needs to add the permissions to a policy and then assign the policy to the user group. To facilitate user permissions management, each cloud service provides some preset policies for you to directly use. If the preset policies cannot meet your requirements of fine-grained permissions management, you can customize policies.

:ref:`Table 1 <en-us_topic_0000002043023008__table16882637182018>` lists all the preset system-defined policies supported by ModelArts.

.. _en-us_topic_0000002043023008__table16882637182018:

.. table:: **Table 1** System-defined policies supported by ModelArts

   +----------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Policy                     | Feature                                                                                                                                           | Type                  |
   +============================+===================================================================================================================================================+=======================+
   | ModelArts FullAccess       | Administrator permissions for ModelArts. Users granted these permissions can operate and use ModelArts.                                           | System-defined policy |
   +----------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | ModelArts CommonOperations | Common user permissions for ModelArts. Users granted these permissions can operate and use ModelArts, but cannot manage dedicated resource pools. | System-defined policy |
   +----------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

Generally, ModelArts FullAccess is assigned only to administrators. If fine-grained management is not required, assigning ModelArts CommonOperations to all users will meet the development requirements of most small teams. If you want to customize policies for fine-grained permissions management, see :ref:`IAM <modelarts_24_0080>`.

.. note::

   When you assign ModelArts permissions to a user, the system does not automatically assign the permissions of other services to the user. This ensures security and prevents unexpected unauthorized operations. In this case, however, you must separately assign permissions of different services to users so that they can perform some ModelArts operations.

   For example, if an IAM user needs to use OBS data for training and the ModelArts training permission has been configured for the IAM user, the IAM user still needs to be assigned with the OBS read, write, and list permissions. The OBS list permission allows you to select the training data path on ModelArts. The read permission is used to preview data and read data for training. The write permission is used to save training results and logs.

   -  For individual users or small organizations, it is a good practice to configure the **Tenant Administrator** policy that applies to global services for IAM users. In this way, IAM users can obtain all user permissions except IAM. However, this may cause security issues. (For an individual user, its default IAM user belongs to the **admin** user group and has the **Tenant Administrator** permission.)
   -  If you want to restrict user operations, configure the minimum permissions of OBS for ModelArts users. For details about fine-grained permissions management of other cloud services, see the corresponding cloud service documents.

ModelArts Agency Authorization
------------------------------

ModelArts must be authorized by users to access other cloud services for AI computing. In the IAM permission system, such authorization is performed through agencies.

To simplify agency authorization, ModelArts supports automatic agency authorization configuration. You only need to configure an agency for yourself or specified users on the **Global Configuration** page of the ModelArts console.

.. note::

   -  Only users with the IAM agency management permission can perform this operation. Generally, members in the IAM admin user group have this permission.
   -  ModelArts agency authorization is region-specific, which means that you must perform agency authorization in each region you use.


.. figure:: /_static/images/en-us_image_0000002043181348.png
   :alt: **Figure 1** Global configuration

   **Figure 1** Global configuration

On the **Global Configuration** page of the ModelArts console, after you click **Add Authorization**, you can configure an agency for a specific user or all users. Generally, an agency named **modelarts_agency_<**\ *Username*\ **>\_**\ *Random ID* is created by default. In the **Permissions** area, you can select the preset permission configuration or select the required policies. If both options cannot meet your requirements, you can create an agency on the IAM management page (you need to delegate ModelArts to access your resources), and then use an existing agency instead of adding an agency on the **Add Authorization** page.

ModelArts associates multiple users with one agency. This means that if two users need to configure the same agency, you do not need to create an agency for each user. Instead, you only need to configure the same agency for the two users.


.. figure:: /_static/images/en-us_image_0000002079180677.png
   :alt: **Figure 2** Mapping between users and agencies

   **Figure 2** Mapping between users and agencies

.. note::

   A user can use ModelArts only after being associated with an agency. However, even if the permissions assigned to the agency are insufficient, no error is reported when the API is called. An error occurs only when the system uses unauthorized functions. For example, you enable message notification when creating a training job. Message notification requires SMN authorization. However, an error occurs only when messages are sent when the training job is running. The system ignores some errors, and other errors may cause job failures. When you implement permission minimization, ensure that you will still have sufficient permissions for the required operations on ModelArts.

Strict Authorization
--------------------

In strict authorization mode, explicit authorization by the account administrator is required for IAM users to access ModelArts. The administrator can add the required ModelArts permissions to common users through authorization policies.

In non-strict authorization mode, IAM users can use ModelArts without explicit authorization. The administrator needs to configure the deny policy for IAM users to prevent them from using some ModelArts functions.

The administrator can change the authorization mode on the **Global Configuration** page.

.. important::

   The strict authorization mode is recommended. In this mode, IAM users must be authorized to use ModelArts functions. In this way, the permission scope of IAM users can be accurately controlled, minimizing permissions granted to IAM users.

Managing Resource Access Using Workspaces
-----------------------------------------

Workspace enables enterprise customers to split their resources into multiple spaces that are logically isolated and to manage access to different spaces. As an enterprise user, you can submit the request for enabling the workspace function to your technical support manager.

After workspace is enabled, a default workspace is created. All resources you have created are in this workspace. A workspace is like a ModelArts twin. You can switch between workspaces in the upper left corner of the ModelArts console. Jobs in different workspaces do not affect each other.

When creating a workspace, you must bind it to an enterprise project. Multiple workspaces can be bound to the same enterprise project, but one workspace cannot be bound to multiple enterprise projects. You can use workspaces for refined restrictions on resource access and permissions of different users. The restrictions are as follows:

-  Users must be authorized to access specific workspaces (this must be configured on the pages for creating and managing workspaces). This means that access to AI assets such as datasets and algorithms can be managed using workspaces.
-  In the preceding permission authorization operations, if you set the scope to enterprise projects, the authorization takes effect only for workspaces bound to the selected projects.

.. note::

   -  Restrictions on workspaces and permission authorization take effect at the same time. That is, a user must have both the permission to access the workspace and the permission to create training jobs (the permission applies to this workspace) so that the user can submit training jobs in this workspace.
   -  If you have enabled an enterprise project but have not enabled a workspace, all operations are performed in the default enterprise project. Ensure that the permissions on the required operations apply to the default enterprise project.
   -  The preceding restrictions do not apply to users who have not enabled any enterprise project.

Summary
-------

Key features of ModelArts permissions management:

-  If you are an individual user, you do not need to consider fine-grained permissions management. Your account has all permissions to use ModelArts by default.
-  All functions of ModelArts are controlled by IAM. You can use IAM authorization to implement fine-grained permissions management for specific users.
-  All users (including individual users) can use specific functions only after agency authorization on ModelArts (**Settings** > **Add Authorization**). Otherwise, unexpected errors may occur.
-  If you have enabled the enterprise project function, you can also enable ModelArts workspace and use both basic authorization and workspace for refined permissions management.

.. |image1| image:: /_static/images/en-us_image_0000002079180673.png
