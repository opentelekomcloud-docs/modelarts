:original_name: modelarts_13_0013.html

.. _modelarts_13_0013:

Failed to Find the Boot File When a Training Job Is Created Using a Custom Image
================================================================================

Symptom
-------

When a custom image was used to create a training job of the old version, error message "No such file or directory" was displayed.

Possible Causes
---------------

The directory of the boot file for running the command is incorrect.

Solution
--------

Perform the following operations to check whether the boot file directory is correct:

On the ModelArts console, select **Custom algorithm** for **Algorithm Type** when creating a training job using a custom image.

If the OBS path to the boot script is **obs://bucket-name/app/code/train.py**, set the code directory to **/bucket-name/app/code/** when creating a job.

After the code directory is configured, run the following command to download the selected **code** folder to the **/home/work/user-job-dir** directory of the old-version training container:

.. code-block::

   bash /home/work/run_train.sh  # Training command of the old version. run_train.sh is the training boot script, which is packed in the base image provided by ModelArts.

Run the following command:

.. code-block::

   bash /home/work/run_train.sh python /home/work/user-job-dir/code/train.py {python_file_parameter}  # Training jobs of the old version
