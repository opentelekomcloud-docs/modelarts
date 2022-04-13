.. _modelarts_08_0002:

Configuring Access Key Authorization
====================================

To use an access key pair for authorization, you need to obtain the access key pair first and then add the access key pair on the ModelArts management console. If your access key pair changes, you need to add a new one.

Obtaining an Access Key
-----------------------

#. On the ModelArts management console, hover over the username in the upper right corner and choose **My Credentials** from the drop-down list.
#. On the **My Credentials** page, choose **Access Keys** > **Create Access Key**.
#. In the **Create Access Key** dialog box that is displayed, enter the verification code received by SMS or email.
#. Click **OK** and save the access key file as prompted. The access key file is saved in the default download folder of the browser. Open the **credentials.csv** file to view the access key (**Access Key Id** and **Secret Access Key**).

Adding an Access Key
--------------------

#. Log in to the ModelArts management console. In the navigation pane, choose **Settings**. The **Settings** page is displayed.

#. Click **Add Authorization**.

#. In the **Add Authorization** dialog box that is displayed, set **Authorization Method** to **AK/SK**. The username is fixed. Enter the obtained access key pair.

   -  **AK**: Enter the value of the **Access Key Id** field in the key file.
   -  **SK**: Enter the value of the **Secret Access Key** field in the key file.

#. Select **I have read and agree to the ModelArts Service Statement** and click **Agree**.

   After the configuration is complete, you can view the access key configurations of an account or IAM user on the **Settings** page.
