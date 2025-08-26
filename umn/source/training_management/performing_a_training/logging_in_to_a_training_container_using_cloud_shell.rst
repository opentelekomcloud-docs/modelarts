:original_name: develop-modelarts-0106.html

.. _develop-modelarts-0106:

Logging In to a Training Container Using Cloud Shell
====================================================

Application Scenario
--------------------

You can use Cloud Shell provided by the ModelArts console to log in to a running training container.

Constraints
-----------

You can use Cloud Shell to log in to a running training container using a dedicated resource pool.

.. _en-us_topic_0000002340727624__section8495153204314:

Preparation: Assigning the Cloud Shell Permission to an IAM User
----------------------------------------------------------------

#. Log in to the management console as a tenant user, hover the cursor over your username in the upper right corner, and choose **Identity and Access Management** from the drop-down list to switch to the IAM management console.

#. .. _en-us_topic_0000002340727624__li1793015304613:

   On the IAM console, choose **Permissions** > **Policies/Roles** from the navigation pane, click **Create Custom Policy** in the upper right corner, and configure the following parameters.

   -  **Policy Name**: Enter a custom policy name, for example, **Using Cloud Shell to log in to a running training container**.
   -  **Policy View**: Select **Visual editor**.
   -  **Policy Content**: Select **Allow**, **ModelArts Service**, **modelarts:trainJob:exec**, and default resources.

#. In the navigation pane, choose **User Groups**. Then, click **Authorize** in the **Operation** column of the target user group. On the **Authorize User Group** page, select the custom policies created in :ref:`2 <en-us_topic_0000002340727624__li1793015304613>`, and click **Next**. Then, select the scope and click **OK**.

   After the configuration, all users in the user group have the permission to use Cloud Shell to log in to a running training container.

   If no user group is available, create a user group, add users using the user group management function, and configure authorization. If the target user is not in a user group, you can add the user to a user group through the user group management function.

Using Cloud Shell
-----------------

#. Configure parameters based on :ref:`Preparation: Assigning the Cloud Shell Permission to an IAM User <en-us_topic_0000002340727624__section8495153204314>`.
#. On the ModelArts console, choose **Training Management** > **Training Jobs**. Go to the details page of the target training job and log in to the training container on the Cloud Shell tab.
