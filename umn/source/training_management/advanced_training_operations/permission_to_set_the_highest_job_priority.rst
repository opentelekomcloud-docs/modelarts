:original_name: develop-modelarts-0082.html

.. _develop-modelarts-0082:

Permission to Set the Highest Job Priority
==========================================

You can configure the priority when you create a training job using a new-version dedicated resource pool. You can change the priority of a pending job. The value ranges from 1 to 3. The default priority is **1**, and the highest priority is **3**. By default, the job priority can be set to **1** or **2**. After the permission to set the highest job priority is configured, the priority can be set to **1** to **3**.

Assigning the Permission to Set the Highest Job Priority to an IAM User
-----------------------------------------------------------------------

#. Log in to the management console as a tenant user, hover the cursor over your username in the upper right corner, and choose **Identity and Access Management** from the drop-down list to switch to the IAM management console.

#. .. _en-us_topic_0000001910016242__li1793015304613:

   On the IAM console, choose **Permissions** > **Policies/Roles** from the navigation pane, click **Create Custom Policy** in the upper right corner, and configure the following parameters.

   -  **Policy Name**: Enter a custom policy name, for example, **Allowing Users to Set the Highest Job Priority**.
   -  **Policy View**: Select **Visual editor**.
   -  **Policy Content**: Select **Allow**, **ModelArts Service**, **modelarts:trainJob:setHighPriority**, and default resources.

#. In the navigation pane, choose **User Groups**. Then, click **Authorize** in the **Operation** column of the target user group. On the **Authorize User Group** page, select the custom policies created in :ref:`2 <en-us_topic_0000001910016242__li1793015304613>`, and click **Next**. Then, select the scope and click **OK**.

   After the configuration, all users in the user group have the permission to use Cloud Shell to log in to a running training container.

   If no user group is available, create a user group, add users using the user group management function, and configure authorization. If the target user is not in a user group, you can add the user to a user group through the user group management function.
