:original_name: modelarts_trouble_0014.html

.. _modelarts_trouble_0014:

Error Message "No such file or directory" Displayed in Training Job Logs
========================================================================

Perform the following operations to locate the fault:

#. :ref:`Checking Whether the Affected Path Is an OBS Path <modelarts_trouble_0014__en-us_topic_0000001147068412_en-us_topic_0000001128983644_section1181277141419>`
#. :ref:`Checking Whether the Affected Path Is Available <modelarts_trouble_0014__en-us_topic_0000001147068412_en-us_topic_0000001128983644_section135339269>`
#. Summary and Suggestions

.. _modelarts_trouble_0014__en-us_topic_0000001147068412_en-us_topic_0000001128983644_section1181277141419:

Checking Whether the Affected Path Is an OBS Path
-------------------------------------------------

When using ModelArts, you need to store data in an OBS bucket. However, the OBS path cannot be used to read data during the execution of the training code.

The reason is as follows:

After a training job is created, the training performance is poor if the running container is directly connected to OBS. To prevent this issue, the system automatically downloads the training data to the local path of the running container. Therefore, an error occurs if an OBS path is used in training code. For example, if the OBS path to the training code is **obs://bucket-A/training/**, the training code will be automatically downloaded to **${MA_JOB_DIR}/training/**.

For example, the OBS path to the training code is **obs://bucket-A/XXX/{training-project}/**, where **{training-project}** is the name of the folder where the training code is stored. During training, the system will automatically download the data from OBS **{training-project}** to the local path of the training container (**$MA_JOB_DIR/{training-project}/**).

If the affected path is a path to the training data, perform the following operations to resolve this issue (see input and output configurations for details):

#. When creating an algorithm, set the code path parameter, which defaults to **data_url**, in the input path mapping configuration.
#. Add a hyperparameter, which defaults to **data_url**, to the training code. Use **data_url** as the local path for inputting the training data.

.. _modelarts_trouble_0014__en-us_topic_0000001147068412_en-us_topic_0000001128983644_section135339269:

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

Summary and Suggestions
-----------------------

Before creating a training job, use the ModelArts development environment to debug the training code to maximally eliminate errors in code migration.
