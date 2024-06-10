:original_name: modelarts_30_0006.html

.. _modelarts_30_0006:

Starting, Stopping, or Deleting a Notebook Instance
===================================================

Starting or Stopping an Instance
--------------------------------

Stop the notebook instances that are not needed. You can also restart a stopped instance.

#. Log in to the ModelArts management console. Choose **DevEnviron** > **Notebook** in the navigation pane on the left. The notebook list of the new version is displayed.
#. Start or stop the target notebook instance.

   -  To start a notebook instance, click **Start** in the **Operation** column of the target notebook instance. Only stopped notebook instances can be started.
   -  To stop a notebook instance, click **Stop** in the **Operation** column of the target notebook instance. Only running notebook instances can be stopped.

      .. caution::

         After a notebook instance is stopped:

         -  The data stored only in **/home/ma-user/work** is retained. For example, the external dependency packages installed in other directories in the development environment will be deleted.

Deleting an Instance
--------------------

Delete the notebook instances that are not needed.

#. Log in to the ModelArts management console. Choose **DevEnviron** > **Notebook** in the navigation pane on the left. The notebook list of the new version is displayed.
#. In the notebook list, click **Delete** in the **Operation** column of the target notebook instance. In the dialog box that is displayed, click **OK**.

   .. caution::

      Deleted notebook instances cannot be recovered.

      After a notebook instance is deleted, the data stored in the mounted directory will be deleted, regardless of whether the notebook instance uses the default storage or an EVS disk for storage.
