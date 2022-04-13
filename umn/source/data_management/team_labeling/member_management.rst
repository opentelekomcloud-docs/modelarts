.. _modelarts_23_0183:

Member Management
=================

There is no member in a new team. You need to add members who will participate in a team labeling task.

A maximum of 100 members can be added to a team. If there are more than 100 members, add them to different teams for better management.

.. _modelarts_23_0183__en-us_topic_0186456618_section060323818470:

Adding a Member
---------------

#. In the left navigation pane of the ModelArts management console, choose **Data Management > Labeling Teams**. The **Labeling Teams** page is displayed.

#. On the **Labeling Teams** page, select a team from the team list on the left and click a team name. The team details are displayed in the right pane.

#. In the **Team Details** area, click **Add Member**.

#. In the displayed **Add Member** dialog box, enter an email address, description, and a role for a member and click **OK**.

   An email address uniquely identifies a team member. Different members cannot use the same email address. The email address you enter will be recorded and saved in ModelArts. It is used only for ModelArts team labeling. After a member is deleted, the email address will also be deleted.

   Possible values of **Role** are **Labeler**, **Reviewer**, and **Team Manager**. Only one **Team Manager** can be set.

   .. _modelarts_23_0183__en-us_topic_0186456618_fig2095294217492:

   .. figure:: /_static/images/en-us_image_0000001156920939.png
      :alt: **Figure 1** Adding a member
   

      **Figure 1** Adding a member

   .. _modelarts_23_0183__en-us_topic_0186456618_fig2953352181118:

   .. figure:: /_static/images/en-us_image_0000001157081267.png
      :alt: **Figure 2** Adding a member
   

      **Figure 2** Adding a member

   Information about the added member is displayed in the **Team Details** area.

Modifying Member Information
----------------------------

You can modify member information if it is changed.

#. In the **Team Details** area, select the desired member.

#. In the row containing the desired member, click **Modify** in the **Operation** column. In the displayed dialog box, modify the description or role.

   The email address of a member cannot be changed. To change the email address of a member, delete the member, and set a new email address when adding a member.

   Possible values of **Role** are **Labeler**, **Reviewer**, and **Team Manager**. Only one **Team Manager** can be set.

Deleting Members
----------------

-  **Deleting a single member**

   In the **Team Details** area, select the desired member, and click **Delete** in the **Operation** column. In the dialog box that is displayed, click **OK**.

-  **Batch Deletion**

   In the **Team Details** area, select members to be deleted and click **Delete**. In the dialog box that is displayed, click **OK**.
