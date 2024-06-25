:original_name: modelarts_08_0007.html

.. _modelarts_08_0007:

Configuring Access Authorization (Global Configuration)
=======================================================

Scenarios
---------

Exposed ModelArts functions are controlled through IAM permissions. For example, if you as an IAM user need to create a training job on ModelArts, you must have the **modelarts:trainJob:create** permission.

ModelArts must access other services for AI computing. For example, ModelArts must access OBS to read your data for training. For security purposes, ModelArts must be authorized to access other cloud services. This is agency authorization.

ModelArts provides one-click auto authorization. You can quickly configure agency authorization on the **Global Configuration** page of ModelArts. Then, ModelArts will automatically create an agency for you and configure it in ModelArts.

In this mode, the authorization scope is specified based on the preset system policies of dependent services to ensure sufficient permissions for using services. The created agency has almost all permissions of dependent services. If you want to precisely control the scope of permissions granted to an agency, use custom authorization. For details about permissions management, see :ref:`Basic Concepts <modelarts_24_0078>`.

This section introduces one-click auto authorization. This mode allows you to grant permissions to IAM users, federated users (virtual IAM users), agencies, and all users with one click.

Constraints
-----------

-  Account

   -  Only a tenant account can perform agency authorization to authorize the current account or all IAM users under the current account.
   -  Multiple IAM users or accounts can use the same agency.
   -  A maximum of 50 agencies can be created under an account.
   -  If you use ModelArts for the first time, add an agency. Generally, common user permissions are sufficient for your requirements. If refined permissions management is required, you can apply for customized permissions.

-  IAM user

   -  If the agency has been authorized, you can view the authorization information on the **Settings** page.
   -  If you have not been authorized, ModelArts will display a message indicating that you have not been authorized when you access the **Add Authorization** page. In this case, contact your administrator to add authorization.

Adding Authorization
--------------------

#. Log in to the ModelArts management console. In the left navigation pane, choose **Settings**. The **Global Configuration** page is displayed.


   .. figure:: /_static/images/en-us_image_0000001946316357.png
      :alt: **Figure 1** Settings

      **Figure 1** Settings

#. Click **Add Authorization**. On the **Add Authorization** page that is displayed, configure the parameters.

   .. table:: **Table 1** Parameters

      +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                              | Description                                                                                                                                                                                                                                                              |
      +========================================+==========================================================================================================================================================================================================================================================================+
      | Authorized User                        | Options: **IAM user**, **Federated user**, **Agency**, and **All users**                                                                                                                                                                                                 |
      |                                        |                                                                                                                                                                                                                                                                          |
      |                                        | -  **IAM user**: You can create IAM users and control their access to certain resources. Every IAM user receives unique login credentials (password and access keys) and is granted resource access according to their permissions.                                      |
      |                                        | -  **Federated user**: A federated user is also called a virtual enterprise user.                                                                                                                                                                                        |
      |                                        | -  **Agency**: You can create agencies in IAM.                                                                                                                                                                                                                           |
      |                                        | -  **All users**: If you select this option, the agency permissions will be granted to all current and future IAM users under the account. For individual users, choose **All users**.                                                                                   |
      +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Authorized To                          | This parameter is not displayed when **Authorized User** is set to **All users**.                                                                                                                                                                                        |
      |                                        |                                                                                                                                                                                                                                                                          |
      |                                        | -  **IAM user**: Select an IAM user and configure an agency for the IAM user.                                                                                                                                                                                            |
      |                                        | -  **Federated user**: Enter the username or user ID of the target federated user.                                                                                                                                                                                       |
      |                                        | -  **Agency**: Select an agency name. You can use account A to create an agency and configure the agency for account B. When using account B, you can switch the role in the upper right corner of the console to account A and use the agency permissions of account A. |
      +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Agency                                 | -  **Use existing**: If there are agencies in the list, select an available one to authorize the selected user. Click the drop-down arrow next to an agency name to view its permission details.                                                                         |
      |                                        | -  **Add agency**: If there is no available agency, create one. If you use ModelArts for the first time, select **Add agency**.                                                                                                                                          |
      +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Add agency > Agency Name               | The system automatically creates a changeable agency name.                                                                                                                                                                                                               |
      +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Add agency > Permissions > Common User | **Common User** provides the permissions to use all basic ModelArts functions. For example, you can access data, and create and manage training jobs. Select this option generally.                                                                                      |
      |                                        |                                                                                                                                                                                                                                                                          |
      |                                        | Click **View permissions** to view common user permissions.                                                                                                                                                                                                              |
      +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Add agency > Permissions > Custom      | If you need refined permissions management, select **Custom** to flexibly assign permissions to the created agency. You can select permissions from the permission list as required.                                                                                     |
      +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Create**.

Viewing Authorized Permissions
------------------------------

You can view the configured authorizations on the **Global Configuration** page. Click **View Permissions** in the **Authorization Content** column to view the permission details.


.. figure:: /_static/images/en-us_image_0000001914601386.png
   :alt: **Figure 2** View Permissions

   **Figure 2** View Permissions

Changing the Authorization Scope
--------------------------------

#. To change the authorization scope, click **Modify permissions in IAM** in the **View Permissions** dialog box.


   .. figure:: /_static/images/en-us_image_0000001914602074.png
      :alt: **Figure 3** Modify permissions in IAM

      **Figure 3** Modify permissions in IAM

#. The agency page of the IAM console is displayed. Modify the agency information on the **Basic Information** tab page. Select your required validity period.

#. On the **Agencies** page, click **Authorize**, select policies or rules, and click **Next**. Select the scope for minimum authorization and click **OK**.

   When setting the minimum authorization scope, you can select either **Global services** or **All resources**. If you select **All resources**, the selected permissions will be applied to all resources.

Deleting Authorization
----------------------

To better manage your authorization, you can delete the authorization of an IAM user or delete the authorizations of all users in batches.

-  **Deleting the authorization of a user**

   On the **Settings** page, the authorizations configured for IAM users under the current account are displayed. You can click **Delete** in the **Operation** column to delete the authorization of a user. After the deletion takes effect, the user cannot use ModelArts functions.

-  **Deleting authorizations in batches**

   On the **Settings** page, click **Delete Authorization** above the authorization list to delete all authorizations of the current account. After the deletion, the account and all IAM users under the account cannot use ModelArts functions.

FAQs
----

#. How do I configure authorization when I use ModelArts for the first time?

   On the **Add Authorization** page, set **Agency** to **Add agency** and select **Common User**, which provides the permissions to use all basic ModelArts functions. For example, you can access data, and create and manage training jobs. Select this option generally.

#. Where is the entrance for authorization using an access key?

   Access key authorization on the global configuration page has been discontinued. If you used an access key for authorization before, switch to agency authorization. To do so, click **Clear Authorization** on the **Global Configuration** page and use an agency for authorization.

#. How do I obtain an access key (AK/SK)?

   You will need to obtain an access key if you are using access key authentication to access certain functions like logging in to PyCharm Toolkit or VS Code, or using real-time services. For details, see :ref:`How Do I Obtain an Access Key? <modelarts_05_0004>`

#. How do I delete an existing agency from the agency list?


   .. figure:: /_static/images/en-us_image_0000001946372881.png
      :alt: **Figure 4** Use existing

      **Figure 4** Use existing

   Go to the IAM console, click **Agencies** in the navigation pane, and delete the target agency.


   .. figure:: /_static/images/en-us_image_0000001914973738.png
      :alt: **Figure 5** IAM console

      **Figure 5** IAM console
