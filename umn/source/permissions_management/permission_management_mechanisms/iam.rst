:original_name: modelarts_24_0080.html

.. _modelarts_24_0080:

IAM
===

This section describes the IAM permission configurations for all ModelArts functions.

IAM Permissions
---------------

If no fine-grained authorization policy is configured for a user created by the administrator, the user has all permissions of ModelArts by default. To control user permissions, the administrator needs to add the user to a user group on IAM and configure fine-grained authorization policies for the user group. In this way, the user obtains the permissions defined in the policies before performing operations on cloud service resources.

You can grant users permissions by using roles and policies.

-  Roles are a type of coarse-grained authorization mechanism that defines permissions related to user responsibilities. Only a limited number of service-level roles are available. When using roles to grant permissions, you must also assign other roles on which the permissions depend to take effect. Roles are not ideal for fine-grained authorization and secure access control.
-  Policies are a type of fine-grained authorization mechanism that defines permissions required to perform operations on specific cloud resources under certain conditions. This type of authorization is more flexible and ideal for secure access control. For example, you can grant ECS users permissions that only allow them to manage a certain type of ECS.

ModelArts does not support role-based authorization. It supports only policy-based authorization.

**Policy Structure**

A policy consists of a version and one or more statements (indicating different actions).


.. figure:: /_static/images/en-us_image_0000001909849928.png
   :alt: **Figure 1** Policy structure

   **Figure 1** Policy structure

**Policy Parameters**

The following describes policy parameters. You can create custom policies by specifying the parameters.

.. table:: **Table 1** Policy parameters

   +------------------------------------------------+-----------------+-------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                      |                 | Description                                                                   | Value                                                                                                                                                                                                             |
   +================================================+=================+===============================================================================+===================================================================================================================================================================================================================+
   | Version                                        |                 | Policy version                                                                | **1.1**: indicates policy-based access control.                                                                                                                                                                   |
   +------------------------------------------------+-----------------+-------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Statement: authorization statement of a policy | Effect          | Whether to allow or deny the operations defined in the action                 | -  **Allow**: indicates the operation is allowed.                                                                                                                                                                 |
   |                                                |                 |                                                                               | -  **Deny**: indicates the operation is not allowed.                                                                                                                                                              |
   |                                                |                 |                                                                               |                                                                                                                                                                                                                   |
   |                                                |                 |                                                                               |    .. note::                                                                                                                                                                                                      |
   |                                                |                 |                                                                               |                                                                                                                                                                                                                   |
   |                                                |                 |                                                                               |       If the policy used to grant user permissions contains both **Allow** and **Deny** for the same action, **Deny** takes precedence.                                                                           |
   +------------------------------------------------+-----------------+-------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                                                | Action          | Operation to be performed on the service                                      | Format: "*Service name*:*Resource type*:*Action*". Wildcard characters (``*``) are supported, indicating all options.                                                                                             |
   |                                                |                 |                                                                               |                                                                                                                                                                                                                   |
   |                                                |                 |                                                                               | Example:                                                                                                                                                                                                          |
   |                                                |                 |                                                                               |                                                                                                                                                                                                                   |
   |                                                |                 |                                                                               | **modelarts:notebook:list**: indicates the permission to view a notebook instance list. **modelarts** indicates the service name, **notebook** indicates the resource type, and **list** indicates the operation. |
   |                                                |                 |                                                                               |                                                                                                                                                                                                                   |
   |                                                |                 |                                                                               | View all actions of a service in its *API Reference*.                                                                                                                                                             |
   +------------------------------------------------+-----------------+-------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                                                | Condition       | Condition for a policy to take effect, including condition keys and operators | Format: "*Condition operator*:{*Condition key*:[*Value 1*,\ *Value 2*]}"                                                                                                                                          |
   |                                                |                 |                                                                               |                                                                                                                                                                                                                   |
   |                                                |                 |                                                                               | If you set multiple conditions, the policy takes effect only when all the conditions are met.                                                                                                                     |
   |                                                |                 |                                                                               |                                                                                                                                                                                                                   |
   |                                                |                 |                                                                               | Example:                                                                                                                                                                                                          |
   |                                                |                 |                                                                               |                                                                                                                                                                                                                   |
   |                                                |                 |                                                                               | **StringEndWithIfExists":{"g:UserName":["specialCharacter"]}**: The statement is valid for users whose names end with **specialCharacter**.                                                                       |
   +------------------------------------------------+-----------------+-------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                                                | Resource        | Resources on which a policy takes effect                                      | Format: *Service name*:*Region*:*Account ID*:*Resource type*:*Resource path*. Wildcard characters (``*``) are supported, indicating all resources.                                                                |
   |                                                |                 |                                                                               |                                                                                                                                                                                                                   |
   |                                                |                 |                                                                               | .. note::                                                                                                                                                                                                         |
   |                                                |                 |                                                                               |                                                                                                                                                                                                                   |
   |                                                |                 |                                                                               |    ModelArts authorization does not allow you to specify a resource path.                                                                                                                                         |
   +------------------------------------------------+-----------------+-------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

ModelArts Resource Types
------------------------

During policy-based authorization, the administrator can select the authorization scope based on ModelArts resource types. The following table lists the resource types supported by ModelArts:

.. table:: **Table 2** ModelArts resource types

   +---------------------+---------------------------------------------------------------------------------------------------------------+
   | Resource Type       | Description                                                                                                   |
   +=====================+===============================================================================================================+
   | notebook            | Notebook instances in DevEnviron                                                                              |
   +---------------------+---------------------------------------------------------------------------------------------------------------+
   | exemlProject        | ExeML projects                                                                                                |
   +---------------------+---------------------------------------------------------------------------------------------------------------+
   | exemlProjectInf     | ExeML-powered real-time inference service                                                                     |
   +---------------------+---------------------------------------------------------------------------------------------------------------+
   | exemlProjectTrain   | ExeML-powered training jobs                                                                                   |
   +---------------------+---------------------------------------------------------------------------------------------------------------+
   | exemlProjectVersion | ExeML project version                                                                                         |
   +---------------------+---------------------------------------------------------------------------------------------------------------+
   | workflow            | Workflow                                                                                                      |
   +---------------------+---------------------------------------------------------------------------------------------------------------+
   | pool                | Dedicated resource pool                                                                                       |
   +---------------------+---------------------------------------------------------------------------------------------------------------+
   | network             | Networking of a dedicated resource pool                                                                       |
   +---------------------+---------------------------------------------------------------------------------------------------------------+
   | trainJob            | Training job                                                                                                  |
   +---------------------+---------------------------------------------------------------------------------------------------------------+
   | trainJobLog         | Runtime logs of a training job                                                                                |
   +---------------------+---------------------------------------------------------------------------------------------------------------+
   | trainJobInnerModel  | Preset model                                                                                                  |
   +---------------------+---------------------------------------------------------------------------------------------------------------+
   | trainJobVersion     | Version of a training job (supported by old-version training jobs that will be discontinued soon)             |
   +---------------------+---------------------------------------------------------------------------------------------------------------+
   | trainConfig         | Configuration of a training job (supported by old-version training jobs that will be discontinued soon)       |
   +---------------------+---------------------------------------------------------------------------------------------------------------+
   | tensorboard         | Visualization job of training results (supported by old-version training jobs that will be discontinued soon) |
   +---------------------+---------------------------------------------------------------------------------------------------------------+
   | model               | Models                                                                                                        |
   +---------------------+---------------------------------------------------------------------------------------------------------------+
   | service             | Real-time service                                                                                             |
   +---------------------+---------------------------------------------------------------------------------------------------------------+
   | nodeservice         | Edge service                                                                                                  |
   +---------------------+---------------------------------------------------------------------------------------------------------------+
   | workspace           | Workspace                                                                                                     |
   +---------------------+---------------------------------------------------------------------------------------------------------------+
   | dataset             | Dataset                                                                                                       |
   +---------------------+---------------------------------------------------------------------------------------------------------------+
   | dataAnnotation      | Dataset labels                                                                                                |
   +---------------------+---------------------------------------------------------------------------------------------------------------+
   | aiAlgorithm         | Algorithm for training jobs                                                                                   |
   +---------------------+---------------------------------------------------------------------------------------------------------------+
   | image               | Image                                                                                                         |
   +---------------------+---------------------------------------------------------------------------------------------------------------+

ModelArts Resource Permissions
------------------------------

For details, see "Permissions Policies and Supported Actions" in *ModelArts API Reference*.
