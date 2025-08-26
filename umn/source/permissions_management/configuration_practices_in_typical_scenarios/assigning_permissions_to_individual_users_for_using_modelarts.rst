:original_name: modelarts_24_0085.html

.. _modelarts_24_0085:

Assigning Permissions to Individual Users for Using ModelArts
=============================================================

Certain ModelArts functions require access to Object Storage Service (OBS), Software Repository for Container (SWR), and Intelligent EdgeFabric (IEF). Before using ModelArts, your account must be authorized to access these services. Otherwise, these functions will be unavailable.

Constraints
-----------

-  Only a tenant account can perform agency authorization to authorize the current account or all IAM users under the current account.
-  Multiple IAM users or accounts can use the same agency.
-  A maximum of 50 agencies can be created under an account.
-  If you use ModelArts for the first time, add an agency. Generally, common user permissions are sufficient for your requirements. You can configure permissions for refined permissions management.
-  If you have not been authorized, ModelArts will display a message indicating that you have not been authorized when you access the **Add Authorization** page. In this case, contact your administrator to add authorization.

.. _en-us_topic_0000002340887384__en-us_topic_0256240291_section2221743101516:

Adding Authorization
--------------------

#. Log in to the ModelArts management console. In the navigation pane on the left, choose **Settings**. The **Global Configuration** page is displayed.


   .. figure:: /_static/images/en-us_image_0000002374845541.png
      :alt: **Figure 1** Global configuration

      **Figure 1** Global configuration

#. Click **Add Authorization**. On the displayed **Add Authorization** page, configure the parameters.

   .. table:: **Table 1** Parameters

      +----------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                                          | Description                                                                                                                                                                                                                                                           |
      +====================================================+=======================================================================================================================================================================================================================================================================+
      | Authorized User                                    | Options: **IAM user**, **Federated user**, **Agency**, and **All users**                                                                                                                                                                                              |
      |                                                    |                                                                                                                                                                                                                                                                       |
      |                                                    | -  **IAM user**: You can create IAM users and control their access to certain resources. Every IAM user receives unique login credentials (password and access keys) and is granted resource access according to their permissions.                                   |
      |                                                    | -  **Federated user**: A federated user is also called a virtual enterprise user.                                                                                                                                                                                     |
      |                                                    | -  **Agency**: You can create agencies in IAM.                                                                                                                                                                                                                        |
      |                                                    | -  **All users**: If you select this option, the agency permissions will be granted to all current and future IAM users under the account. For individual users, choose **All users**.                                                                                |
      +----------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Authorized To                                      | This parameter is not displayed when **Authorized User** is set to **All users**.                                                                                                                                                                                     |
      |                                                    |                                                                                                                                                                                                                                                                       |
      |                                                    | -  **IAM user**: Select an IAM user and configure an agency for the IAM user.                                                                                                                                                                                         |
      |                                                    | -  **Federated user**: Enter the username or user ID of the target federated user.                                                                                                                                                                                    |
      |                                                    | -  **Agency**: Select an agency name. You can create an agency under account A and grant the agency permissions to account B. When using account B, you can switch to account A in the upper right corner of the console and use the agency permissions of account A. |
      +----------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | **Agency**                                         | -  **Use existing**: If there are agencies in the list, select an available one to authorize the selected user. Click the drop-down arrow next to an agency name to view its permission details.                                                                      |
      |                                                    | -  **Add agency**: If there is no available agency, create one. If you use ModelArts for the first time, select **Add agency**.                                                                                                                                       |
      +----------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | **Add agency** > **Agency Name**                   | The system automatically creates an agency name that is editable.                                                                                                                                                                                                     |
      +----------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | **Add agency** > **Permissions** > **Common User** | You can use basic ModelArts functions, for example, accessing data and creating and managing training jobs. Select this option generally.                                                                                                                             |
      |                                                    |                                                                                                                                                                                                                                                                       |
      |                                                    | Click **View permissions** to view common user permissions.                                                                                                                                                                                                           |
      +----------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | **Add agency** > **Permissions** > **Custom**      | If you need refined permissions management, select **Custom** to flexibly assign permissions to the created agency. You can select permissions from the permission list as required.                                                                                  |
      +----------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Create**.

Viewing Authorized Permissions
------------------------------

You can view the authorization content on the **Global Configuration** page. Click **View Permissions** in the **Authorization Content** column to view the permission details.


.. figure:: /_static/images/en-us_image_0000002340887464.png
   :alt: **Figure 2** View Permissions

   **Figure 2** View Permissions
