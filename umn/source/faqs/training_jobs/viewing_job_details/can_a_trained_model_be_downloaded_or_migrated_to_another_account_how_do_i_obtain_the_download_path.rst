:original_name: modelarts_05_0121.html

.. _modelarts_05_0121:

Can a Trained Model Be Downloaded or Migrated to Another Account? How Do I Obtain the Download Path?
====================================================================================================

You can download the model trained by a training job and upload the downloaded model to OBS in the region corresponding to the target account.

Obtaining a Model Download Path
-------------------------------

#. Log in to the ModelArts console. In the left navigation pane, choose **Training Management** > **Training Jobs**. The **Training Jobs** page is displayed.
#. In the training job list, click a job name to view job details.
#. On the **Configurations** tab page, obtain the path specified for **Training Output Path**, that is, the download path of the training model.

Migrating the Model to Another Account
--------------------------------------

There are two ways to migrate a trained model to another account:

-  Download the trained model and then upload it to the OBS bucket in the region corresponding to the target account.
-  Configure a policy for the folder or bucket where the model is stored to authorize other accounts to perform read and write operations. For details, see "Creating a Custom Bucket Policy (Visual Editor)" in OBS documentation.
