:original_name: modelarts_24_0097.html

.. _modelarts_24_0097:

Prohibiting a User from Using a Public Resource Pool
====================================================

This section describes how to control the ModelArts permissions of a user so that the user is not allowed to use a public resource pool to create training jobs, create notebook instances, or deploy inference services.

Context
-------

Through permission control, ModelArts dedicated resource pool users can be prohibited from using a public resource pool to create training jobs, create notebook instances, or deploy inference services.

To control the permissions, configure the following permission policy items:

-  **modelarts:notebook:create**: allows you to create a notebook instance.
-  **modelarts:trainJob:create**: allows you to create a training job.
-  **modelarts:service:create**: allows you to create an inference service.

Procedure
---------

#. Log in to the management console as a tenant user, hover the cursor over your username in the upper right corner, and choose **Identity and Access Management** from the drop-down list to switch to the IAM management console.

#. .. _en-us_topic_0000002233739116__li1793015304613:

   In the navigation pane, choose **Permissions** > **Policies/Roles**. On the **Policies/Roles** page, click **Create Custom Policy** in the upper right corner, configure parameters, and click **OK**.

   -  **Policy Name**: Configure the policy name.

   -  **Policy View**: Select **Visual editor** or **JSON**.

   -  **Policy Content**: Select **Deny**. In **Select service**, search for **ModelArts** and select it. In **ReadWrite** under **Actions**, search for **modelarts:trainJob:create**, **modelarts:notebook:create**, and **modelarts:service:create** and select them. **All**: Retain the default setting. In **Add request condition**, click **Add Request Condition**. In the displayed dialog box, set **Condition Key** to **modelarts:poolType**, **Operator** to **StringEquals**, and **Value** to **public**.

      The policy content in JSON view is as follows:

      .. code-block::

         {
             "Version": "1.1",
             "Statement": [
                 {
                     "Effect": "Deny",
                     "Action": [
                         "modelarts:trainJob:create",
                         "modelarts:notebook:create",
                         "modelarts:service:create"
                     ],
                     "Condition": {
                         "StringEquals": {
                             "modelarts:poolType": [
                                 "public"
                             ]
                         }
                     }
                 }
             ]
         }

#. In the navigation pane, choose **User Groups**. On the **User Groups** page, locate the row containing the target user group and click **Authorize** in the **Operation** column. On the **Authorize User Group** page, select the custom policy created in :ref:`2 <en-us_topic_0000002233739116__li1793015304613>` and click **Next**. Then, select the scope and click **OK**.

   After the configuration, all users in the user group have the permission to view all notebook instances created by users in the user group.

   If no user group is available, create one, add users to it through user group management, and configure authorization for the user group. If the target user is not in a user group, add the user to a user group through user group management.

#. Add the policy to the user's agency authorization. This prevents the user from breaking the permission scope through a token on the tenant plane.

   In the navigation pane, choose **Agencies**. Locate the agency used by the user group on ModelArts and click **Modify** in the **Operation** column. In the **Permissions** tab, click **Authorize**, select the created custom policy, and click **Next**. Select the scope for authorization and click **OK**.

Verification
------------

Log in to the ModelArts console as an IAM user, choose **Training Management** > **Training Jobs**, and click **Create Training Job**. On the page for creating a training job, only a dedicated resource pool can be selected for **Resource Pool**.

Log in to the ModelArts console as an IAM user, choose **DevEnviron** > **Notebook**, and click **Create**. On the page for creating a notebook instance, only a dedicated resource pool can be selected for **Resource Pool**.

Log in to the ModelArts console as an IAM user, choose **Service Deployment** > **Real-Time Services**, and click **Deploy**. On the page for service deployment, only a dedicated resource pool can be selected for **Resource Pool**.
