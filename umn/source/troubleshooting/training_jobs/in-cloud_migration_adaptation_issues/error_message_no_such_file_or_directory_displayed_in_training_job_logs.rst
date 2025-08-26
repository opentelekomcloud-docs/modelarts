:original_name: modelarts_trouble_0014.html

.. _modelarts_trouble_0014:

Error Message "No such file or directory" Displayed in Training Job Logs
========================================================================

Symptom
-------

If a training job failed, error message "No such file or directory" is displayed in logs.

If a training input path is unreachable, error message "No such file or directory" is displayed.

If a training boot file is unavailable, error message "No such file or directory" is displayed.


.. figure:: /_static/images/en-us_image_0000002374846813.png
   :alt: **Figure 1** Example log for an unavailable training boot file

   **Figure 1** Example log for an unavailable training boot file

Possible Causes
---------------

-  If the training input path is unreachable, the path is incorrect. Perform the following operations to locate the fault:

   #. :ref:`Checking Whether the Affected Path Is an OBS Path <en-us_topic_0000002374845653__en-us_topic_0000001128983644_section1181277141419>`
   #. :ref:`Checking Whether the Affected Path Is Available <en-us_topic_0000002374845653__en-us_topic_0000001128983644_section135339269>`

-  If the training boot file is unavailable, the path to the training job boot command is incorrect. Rectify the fault by referring to :ref:`Checking the File Boot Path of a Training Job Created Using a Custom Image <en-us_topic_0000002374845653__en-us_topic_0000001128983644_section1193319591840>`.
-  Multiple processes or workers read and write the same file. If SFS is used, check whether multiple nodes concurrently write the same file. Analyze the code and check whether multiple processes write the same file. It is a good practice to prevent multiple processes or nodes from concurrently reading and writing the same file.

.. _en-us_topic_0000002374845653__en-us_topic_0000001128983644_section1181277141419:

Checking Whether the Affected Path Is an OBS Path
-------------------------------------------------

When using ModelArts, store data in an OBS bucket. However, the OBS path cannot be used to read data during the execution of the training code.

The reason is as follows:

After a training job is created, the training performance is poor if the running container is directly connected to OBS. To prevent this issue, the system automatically downloads the training data to the local path of the running container. Therefore, an error occurs if an OBS path is used in training code. For example, if the OBS path to the training code is **obs://bucket-A/training/**, the training code will be automatically downloaded to **${MA_JOB_DIR}/training/**.

For example, the OBS path to the training code is **obs://bucket-A/XXX/{training-project}/**, where **{training-project}** is the name of the folder where the training code is stored. During training, the system will automatically download the data from OBS **{training-project}** to the local path of the training container (**$MA_JOB_DIR/{training-project}/**).

If the affected path is a path to the training data, perform the following operations to resolve this issue (see "input and output configurations" for details):

#. When creating an algorithm, set the code path parameter, which defaults to **data_url**, in the input path mapping configuration.
#. Add a hyperparameter, which defaults to **data_url**, to the training code. Use **data_url** as the local path for inputting the training data.

.. _en-us_topic_0000002374845653__en-us_topic_0000001128983644_section135339269:

Checking Whether the Affected Path Is Available
-----------------------------------------------

The code developed locally needs to be uploaded to the ModelArts backend. It is likely to incorrectly set the path to a dependency file in training code.

You are suggested to use the following general solution to obtain the absolute path to a dependency file through the OS API.

Example:

.. code-block::

   |---project_root                # Root directory for code
      |---BootfileDirectory        # Directory where the boot file is located
        |---bootfile.py            # Boot file
      |---otherfileDirectory       # Directory where other dependency files are located
        |---otherfile.py           # Other dependency files

Do as follows to obtain the path to a dependency file, **otherfile_path** in this example, in the boot file:

.. code-block::

   import os
   current_path = os.path.dirname(os.path.realpath(__file__)) # Directory where the boot file is located
   project_root = os.path.dirname(current_path) # Root directory of the project, which is the code directory set on the ModelArts training console
   otherfile_path = os.path.join(project_root, "otherfileDirectory", "otherfile.py")

.. _en-us_topic_0000002374845653__en-us_topic_0000001128983644_section1193319591840:

Checking the File Boot Path of a Training Job Created Using a Custom Image
--------------------------------------------------------------------------

Take OBS path **obs://obs-bucket/training-test/demo-code** as an example. The training code in this path will be automatically downloaded to **${MA_JOB_DIR}/demo-code** in the training container, where **demo-code** is the last-level directory of the OBS path and can be customized.

If you use a custom image to create a training job, the system will automatically run the image boot command after the code directory is downloaded. The boot command must comply with the following rules:

-  If the training startup script is a .py file, **train.py** for example, the boot command can be **python ${MA_JOB_DIR}/demo-code/train.py**.
-  If the training startup script is an .sh file, **main.sh** for example, the boot command can be **bash ${MA_JOB_DIR}/demo-code/main.sh**, where **demo-code** is the last-level directory of the OBS path and can be customized.

Summary and Suggestions
-----------------------

Before creating a training job, use the ModelArts development environment to debug the training code to maximally eliminate errors in code migration.
