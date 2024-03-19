:original_name: modelarts_08_0007.html

.. _modelarts_08_0007:

Configuring Access Authorization (Global Configuration)
=======================================================

Certain ModelArts functions require access to Object Storage Service (OBS), Software Repository for Container (SWR), and Intelligent EdgeFabric (IEF). Before using ModelArts, your account must be authorized to access these services. Otherwise, these functions will be unavailable.

Before You Start
----------------

-  Account

   -  Only a cloud account can use an agency to authorize the current account or all IAM users under the current account.
   -  Multiple IAM users or accounts can use the same agency.
   -  A maximum of 50 agencies can be created under an account.
   -  If you use ModelArts for the first time, add an agency. Generally, common user permissions are sufficient for your requirements. If refined permissions management is required, you can apply for customized permissions.

-  IAM user

   -  If the agency has been authorized, you can view the authorization information on the **Settings** page.
   -  If you have not been authorized, ModelArts will display a message indicating that you have not been authorized when you access the **Add Authorization** page. In this case, contact your administrator to add authorization.

Adding Authorization
--------------------

#. Log in to the ModelArts management console. In the left navigation pane, choose **Settings**. The **Global Configuration** page is displayed.


   .. figure:: /_static/images/en-us_image_0000001851786845.png
      :alt: **Figure 1** Settings

      **Figure 1** Settings

#. Click **Add Authorization**. On the **Add Authorization** page that is displayed, configure the parameters.


   .. figure:: /_static/images/en-us_image_0000001852592981.png
      :alt: **Figure 2** Add Authorization

      **Figure 2** Add Authorization

   .. table:: **Table 1** Parameters

      +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                              | Description                                                                                                                                                                                            |
      +========================================+========================================================================================================================================================================================================+
      | Username                               | By default, **All users** is selected, which indicates that all users, including the current account in the drop-down list will be authorized. You can also select a username from the drop-down list. |
      +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Agency                                 | -  **Use existing**: If there are agencies in the list, select an available one to authorize the selected user. Click the drop-down arrow next to an agency name to view its permission details.       |
      |                                        | -  **Add agency**: If there is no available agency, create one. If you use ModelArts for the first time, select **Add agency**.                                                                        |
      +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Add agency > Agency Name               | The system automatically creates a changeable agency name.                                                                                                                                             |
      +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Add agency > Permissions > Common User | **Common User** provides the permissions to use all basic ModelArts functions. For example, you can access data, and create and manage training jobs. Select this option generally.                    |
      |                                        |                                                                                                                                                                                                        |
      |                                        | Click **View permissions** to view common user permissions.                                                                                                                                            |
      +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Add agency > Permissions > Custom      | If you need refined permissions management, select **Custom** to flexibly assign permissions to the created agency. You can select permissions from the permission list as required.                   |
      +----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Create**.

Viewing Authorized Permissions
------------------------------

You can view the configured authorizations on the **Global Configuration** page. Click **View Permissions** in the **Authorization Content** column to view the permission details.


.. figure:: /_static/images/en-us_image_0000001852712909.png
   :alt: **Figure 3** View Permissions

   **Figure 3** View Permissions


.. figure:: /_static/images/en-us_image_0000001805228246.png
   :alt: **Figure 4** List of common user permissions

   **Figure 4** List of common user permissions

Changing the Authorization Scope
--------------------------------

#. If you want to modify the authorization, click **Modify permissions in IAM** in the the **View Permissions** dialog box.


   .. figure:: /_static/images/en-us_image_0000001851867269.png
      :alt: **Figure 5** Modify permissions in IAM

      **Figure 5** Modify permissions in IAM

#. The agency page of the IAM console is displayed. Modify the agency information on the **Basic Information** tab page. Select your required validity period.


   .. figure:: /_static/images/en-us_image_0000001851867781.png
      :alt: **Figure 6** Agency information

      **Figure 6** Agency information

#. On the **Agencies** page, click **Authorize**, select policies or rules, and click **Next**. Select the scope for minimum authorization and click **OK**.

   When setting the minimum authorization scope, you can select either **Global services** or **All resources**. If you select **All resources**, the selected permissions will be applied to all resources. .

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

   Access key authorization on the global configuration page has been discontinued. If you used an access key for authorization before, switch to agency authorization. On the **Global Configuration** page, click **Clear Authorization**, and use agencies for authorization.

#. How do I obtain an access key (AK/SK)?

   If you use access key authentication to use certain functions, such as accessing real-time services through PyCharm Toolkit or VS Code, obtain an access key. For details, see :ref:`How Do I Obtain an Access Key? <modelarts_05_0004>`

#. How do I delete an existing agency from the agency list?


   .. figure:: /_static/images/en-us_image_0000001805229686.png
      :alt: **Figure 7** Use existing

      **Figure 7** Use existing

   Go to the agency page of the IAM console and delete the target agency.


   .. figure:: /_static/images/en-us_image_0000001851868941.png
      :alt: **Figure 8** IAM console

      **Figure 8** IAM console
