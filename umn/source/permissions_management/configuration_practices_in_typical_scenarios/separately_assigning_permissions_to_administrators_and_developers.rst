:original_name: modelarts_24_0093.html

.. _modelarts_24_0093:

Separately Assigning Permissions to Administrators and Developers
=================================================================

In small- and medium-sized teams, administrators need to globally control ModelArts resources, and developers only need to focus on their own instances. By default, a developer account does not have the **te_admin** permission. The tenant account must configure the required permissions. This section uses notebook as an example to describe how to assign different permissions to administrators and developers through custom policies.

Scenarios
---------

To develop a project using notebook, administrators need full control permissions for using ModelArts dedicated resource pools, and access and operation permissions on all notebook instances.

To use development environments, developers only need operation permissions for using their own instances and dependent services. They do not need to perform operations on ModelArts dedicated resource pools or view notebook instances of other users.


.. figure:: /_static/images/en-us_image_0000001943969601.png
   :alt: **Figure 1** Account relationships

   **Figure 1** Account relationships

Configuring Permissions for an Administrator
--------------------------------------------

Assign full control permissions to administrators for using ModelArts dedicated resource pools and all notebook instances. The procedure is as follows:

#. Use a tenant account to create an administrator user group **ModelArts_admin_group** and add administrator accounts to **ModelArts_admin_group**.

#. .. _en-us_topic_0000001910009780__li58484438106:

   Create a custom policy.

   a. Log in to the management console using an administrator account, hover over your username in the upper right corner, and click **Identity and Access Management** from the drop-down list to switch to the IAM management console.

   b. .. _en-us_topic_0000001910009780__li284812437102:

      Create custom policy 1 and assign IAM and OBS permissions to the user. In the navigation pane of the IAM console, choose **Permissions** > **Policies/Roles**. Click **Create Custom Policy** in the upper right corner. On the displayed page, enter **Policy1_IAM_OBS** for **Policy Name**, select **JSON** for **Policy View**, configure the policy content, and click **OK**.

      The custom policy **Policy1_IAM_OBS** is as follows, which grants IAM and OBS operation permissions to the user. You can directly copy and paste the content.

      .. code-block::

         {
             "Version": "1.1",
             "Statement": [
                 {
                     "Effect": "Allow",
                     "Action": [
                         "iam:users:listUsers",
                         "iam:projects:listProjects",
                         "obs:object:PutObject",
                         "obs:object:GetObject",
                         "obs:object:GetObjectVersion",
                         "obs:bucket:HeadBucket",
                         "obs:object:DeleteObject",
                         "obs:bucket:CreateBucket",
                         "obs:bucket:ListBucket"
                         ]
                 }
             ]
         }

   c. Repeat :ref:`2.b <en-us_topic_0000001910009780__li284812437102>` to create custom policy 2 and grant the user the permissions to perform operations on dependent services ECS, SWR, MRS, and SMN as well as ModelArts. Set **Policy Name** to **Policy2_AllowOperation** and **Policy View** to **JSON**, configure the policy content, and click **OK**.

      The custom policy **Policy2_AllowOperation** is as follows, which grants the user the permissions to perform operations on dependent services ECS, SWR, MRS, and SMN as well as ModelArts. You can directly copy and paste the content.

      .. code-block::

         {
             "Version": "1.1",
             "Statement": [
                 {
                     "Effect": "Allow",
                     "Action": [
                         "ecs:serverKeypairs:list",
                         "ecs:serverKeypairs:get",
                         "ecs:serverKeypairs:delete",
                         "ecs:serverKeypairs:create",
                         "swr:repository:getNamespace",
                         "swr:repository:listNamespaces",
                         "swr:repository:deleteTag",
                         "swr:repository:getRepository",
                         "swr:repository:listTags",
                         "swr:instance:createTempCredential",
                         "mrs:cluster:get",
                         "modelarts:*:*"
                     ]
                 }
             ]
         }

#. Grant the policy created in :ref:`2 <en-us_topic_0000001910009780__li58484438106>` to the administrator group **ModelArts_admin_group**.

   a. In the navigation pane of the IAM console, choose **User Groups**. On the **User Groups** page, locate the row that contains **ModelArts_admin_group**, click **Authorize** in the **Operation** column, and select **Policy1_IAM_OBS** and **Policy2_AllowOperation**. Click **Next**.
   b. Specify the scope as **All resources** and click **OK**.

#. Configure agent-based ModelArts access authorization for an administrator to allow ModelArts to access dependent services such as OBS.

   a. Log in to the ModelArts management console using a tenant account. In the navigation pane, choose **Settings**. The **Global Configuration** page is displayed.
   b. Click **Add Authorization**. On the **Add Authorization** page, set **Authorized User** to **IAM user**, select an administrator account for **Authorized To**, select **Add agency**, and select **Common User** for **Permissions**. Permissions control is not required for administrators, so use default setting **Common User**.
   c. Click **Create**.

#. Test administrator permissions.

   a. Log in to the ModelArts management console as the administrator. On the login page, ensure that **IAM User Login** is selected.

      Change the password as prompted upon the first login.

   b. In the navigation pane of the ModelArts management console, choose **Dedicated Resource Pools** and click **Create**. If the console does not display a message indicating insufficient permissions, the permissions have been assigned to the administrator.

Configuring Permissions for a Developer
---------------------------------------

Use IAM for fine-grained control of developer permissions. The procedure is as follows:

#. Use a tenant account to create a developer user group **user_group** and add developer accounts to **user_group**.
#. Create a custom policy.

   a. Log in to the management console using a tenant account, hover over your username in the upper right corner, and click **Identity and Access Management** from the drop-down list to switch to the IAM management console.

   b. Create custom policy 3 to prevent users from performing operations on ModelArts dedicated resource pools and viewing notebook instances of other users.

      In the navigation pane of the IAM console, choose **Permissions** > **Policies/Roles**. Click **Create Custom Policy** in the upper right corner. On the displayed page, enter **Policy3_DenyOperation** for **Policy Name**, select **JSON** for **Policy View**, configure the policy content, and click **OK**.

      The custom policy **Policy3_DenyOperation** is as follows. You can copy and paste the content.

      .. code-block::

         {
             "Version": "1.1",
             "Statement": [
                 {
                     "Effect": "deny",
                     "Action": [
                         "modelarts:pool:create",
                         "modelarts:pool:update",
                         "modelarts:pool:delete",
                 "modelarts:notebook:listAllNotebooks"
                     ]

                 }
             ]
         }

#. Grant the custom policy to the developer user group **user_group**.

   a. In the navigation pane of the IAM console, choose **User Groups**. On the **User Groups** page, locate the row that contains **user_group**, click **Authorize** in the **Operation** column, and select **Policy1_IAM_OBS**, **Policy2_AllowOperation**, and **Policy3_DenyOperation**. Click **Next**.
   b. Specify the scope as **All resources** and click **OK**.

#. Configure agent-based ModelArts access authorization for a developer to allow ModelArts to access dependent services such as OBS.

   a. Log in to the ModelArts management console using a tenant account. In the navigation pane, choose **Settings**. The **Global Configuration** page is displayed.

   b. Click **Add Authorization**. On the **Add Authorization** page, set **Authorized User** to **IAM user**, select a developer account for **Authorized To**, add an agency **ma_agency_develop_user**, set **Permissions** to **Custom**, and select **OBS Administrator**. Developers only need OBS authorization to allow developers to access OBS when using notebook.

   c. Click **Create**.

   d. On the **Global Configuration** page, click **Add Authorization** again. On the **Add Authorization** page that is displayed, configure an agency for other developer users.

      On the **Add Authorization** page, set **Authorized User** to **IAM user**, select a developer account for **Authorized To**, and select the existing agency **ma_agency_develop_user** created before.

#. Test developer permissions.

   a. Log in to the ModelArts management console as an IAM user in **user_group**. On the login page, ensure that **IAM User Login** is selected.

      Change the password as prompted upon the first login.

   b. In the navigation pane of the ModelArts management console, choose **Dedicated Resource Pools** and click **Create**. If the console does not display a message indicating insufficient permissions, the permissions have been assigned to the developer.
