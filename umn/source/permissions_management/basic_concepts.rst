.. _modelarts_23_0078:

Basic Concepts
==============

A fine-grained policy is a set of permissions defining which operations on which cloud services can be performed. Each policy can define multiple permissions. After a policy is granted to a user group, users in the group can obtain all permissions defined by the policy. IAM implements fine-grained permissions management based on the permissions defined by policies.

IAM supports two types of policies:

-  Default policies: Define the common permissions preset in the system, which are typically read-only or management permissions for cloud services such as ModelArts. Default policies can be used only for authorization and cannot be edited or modified.
-  Custom policies: Define the permissions created and managed by users and are the extension and supplement of default policies.
