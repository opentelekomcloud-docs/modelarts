:original_name: modelarts_01_0017.html

.. _modelarts_01_0017:

Permissions Management
======================

If you need to assign different permissions to different employees in your enterprise to access ModelArts resources, IAM is a good choice for fine-grained permissions management.

Granting Permissions to Users
-----------------------------


.. figure:: /_static/images/en-us_image_0000001404986026.png
   :alt: **Figure 1** Authorization model

   **Figure 1** Authorization model

#. Plan user groups and grant required permissions to each user group.
#. Add a user to a specific user group so that the user can inherit the permissions of the group.

When personnel changes occur, you only need to change individual user permissions by changing their user group. User groups make permission management more efficient.

Granting Permissions to Other Accounts
--------------------------------------

You (account A) can create an agency on IAM to grant required permissions to the delegated account (account B). The administrator of account B grants the **Agent Operator** permissions to the user of account B to enable the user to manage resources in your account (account A).

Granting Permissions to Federated Users
---------------------------------------

You can use IAM to create an IdP and create rules for the IdP to convert federated users into IAM users who have specified permissions to access cloud resources.


.. figure:: /_static/images/en-us_image_0000001455265885.png
   :alt: **Figure 2** Principles of identity conversion for federated users

   **Figure 2** Principles of identity conversion for federated users
