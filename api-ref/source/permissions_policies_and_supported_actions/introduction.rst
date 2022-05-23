:original_name: modelarts_03_0146.html

.. _modelarts_03_0146:

Introduction
============

This section describes fine-grained permissions management for your ModelArts. If your current account does not require individual IAM users, skip this section.

By default, new IAM users do not have permissions assigned. You need to add a user to one or more groups, and attach permissions policies or roles to these groups. Users inherit permissions from the groups to which they are added and can perform specified operations on cloud services based on the permissions.

.. note::

   Policy-based authorization is useful if you want to allow or deny the access to an API.

An account has all the permissions required to call all APIs, but IAM users must be assigned the required permissions. The permissions required for calling an API are determined by the actions supported by the API. Only users who have been granted permissions allowing the actions can call the API successfully. For example, if an IAM user wants to query ECSs using an API, the user must have been granted permissions that allow the **modelarts:notebook:create** action.

Supported Actions
-----------------

ModelArts provides system-defined policies that can be directly used in IAM. You can also create custom policies and use them to supplement system-defined policies, implementing more refined access control. Operations supported by policies are specific to APIs. The following are common concepts related to policies:

-  Permissions: Statements in a policy that allow or deny certain operations.
-  APIs: RESTful APIs that can be called in a custom policy.

-  Actions: Specific operations that are allowed or denied.
-  Related actions: Actions on which a specific action depends to take effect. When assigning permissions for the action to a user, you also need to assign permissions for the related actions.
-  IAM or enterprise projects: Type of projects for which an action will take effect. Policies that contain actions for both IAM and enterprise projects can be used and take effect for both IAM and Enterprise Management. Policies that only contain actions for IAM projects can be used and only take effect for IAM.

   .. note::

      The check mark (Y) and cross symbol (x) indicate that an action takes effect or does not take effect for the corresponding type of projects.
