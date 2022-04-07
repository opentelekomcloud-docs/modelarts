.. _modelarts_08_0007:

Configuring Agency Authorization (Recommended)
==============================================

An agency is used to delegate ModelArts the operation permissions for dependent services such as OBS and SWR. Before using ModelArts, you need to complete agency authorization.

.. note::

   If you have used ModelArts before, click **Delete Authorization** in the global configurations area and then create an agency.

Before You Start
----------------

-  account

   -  Only a cloud account can perform agency authorization to authorize the current account or all IAM users under the current account.
   -  Multiple IAM users or accounts can use the same agency.
   -  A maximum of 50 agencies can be created under an account.

-  IAM user

   -  If the agency has been authorized, you can view the authorization information on the **Settings** page.
   -  If an IAM user has not obtained the authorization, ModelArts will display a message indicating that the user has not been authorized when the user accesses the **Add Authorization** page. In this case, contact the administrator of the IAM user to add authorization. Alternatively, you can :ref:`use access keys for authorization <modelarts_08_0002>`.

-  When configuring an agency, you can use an automatically created agency. For details, see :ref:`Automatically Creating an IAM Agency <modelarts_08_0007__en-us_topic_0284258827_en-us_topic_0256240291_section19256347172519>`. You can also configure an agency. For example, you can configure an IAM user with the agency valid for only one day.

Configuring Authorization
-------------------------

#. Log in to the ModelArts management console. In the left navigation pane, click **Settings**. The **Settings** page is displayed.

#. Click **Add Authorization**.

#. In the **Add Authorization** dialog box that is displayed, set **Authorization Method** to **Agency**, and select the username and agency to be authorized.

   .. table:: **Table 1** Parameters

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                                                                          |
      +===================================+======================================================================================================================================================================================================================================================================================================================================================================================================================================+
      | Authorization Method              | Select **Agency**.                                                                                                                                                                                                                                                                                                                                                                                                                   |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Username                          | Select an account from the drop-down list on the right. By default, **All IAM users (including logged-in account)** is selected, which indicates that authorization will be performed for the logged-in account and all IAM users under the account. All IAM users under the logged-in account are displayed in the drop-down list. You can configure an agency for an IAM user.                                                     |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Agency                            | -  **Auto Create** (recommended): When you use ModelArts **Settings** for the first time, no agency is available. In this case, you can click **Auto Create** to automatically create an agency for the user selected in **Username**. For details about the automatically created agency, see :ref:`Automatically Creating an IAM Agency <modelarts_08_0007__en-us_topic_0284258827_en-us_topic_0256240291_section19256347172519>`. |
      |                                   | -  Select an existing agency: If you have created agencies in IAM, you can select an available agency from the drop-down list to authorize the selected user.                                                                                                                                                                                                                                                                        |
      |                                   | -  **Create on IAM**: If the automatically created agency cannot meet your requirements, you can click **Create on IAM** to manually create an agency on the IAM management console. If you choose **Create on IAM**, configure at least the **ModelArts CommonOperation** and **OBS Operate Access** permissions. Otherwise, the basic functions of ModelArts will be unavailable.                                                  |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. After configuring the username and agency, select **I have read and agree to the ModelArts Service Statement** and click **Agree**.

   After the configuration is complete, you can view the agency configurations of an account or IAM user on the **Settings** page.

.. _modelarts_08_0007__en-us_topic_0284258827_en-us_topic_0256240291_section19256347172519:

Automatically Creating an IAM Agency
------------------------------------

The following provides the details about the agency automatically created by ModelArts.

-  **Agency Name**: For a cloud account, the agency name is **modelarts_agency**. For an IAM user, the agency name is **ma_agency_<IAM username>**.
-  **Agency Type**: Select **Cloud service**.
-  **Cloud Service**: Select **ModelArts**.
-  **Validity Period**: Select **Unlimited**.
-  **Permissions**: The **ModelArts CommonOperations**, **OBS OperateAccess**, and **Tenant Administrator** (required for using other dependent services) permissions are automatically added for this agency to use all ModelArts functions.

Deleting Authorizations
-----------------------

To better manage your authorization, you can delete the authorization of an IAM user or delete the authorizations of all users in batches.

-  **Deleting the authorization of a user**

   On the **Settings** page, the authorizations configured for IAM users under the current account are displayed. You can click **Delete** in the **Operation** column to delete the authorization of a user. After the deletion takes effect, the user cannot use ModelArts functions.

-  **Deleting authorizations in batches**

   On the **Settings** page, click **Delete Authorization** above the authorization list to delete all authorizations of the current account. After the deletion, the account and all IAM users under the account cannot use ModelArts functions.
