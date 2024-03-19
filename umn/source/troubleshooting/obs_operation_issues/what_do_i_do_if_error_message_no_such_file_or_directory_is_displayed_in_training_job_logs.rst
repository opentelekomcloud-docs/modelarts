:original_name: modelarts_05_0032.html

.. _modelarts_05_0032:

What Do I Do If Error Message "No such file or directory" Is Displayed in Training Job Logs?
============================================================================================

When you use ModelArts, your data is stored in an OBS bucket. There is an OBS path to your data, for example, **bucket_name/dir/image.jpg**. ModelArts training jobs run in containers, and the jobs access OBS data through the OBS path to the data. If the file or path is unavailable, it is possible that the data storage path was incorrectly configured when you created the training job, or that the access path in the code file is incorrect.

Perform the following operations to locate the fault:

#. :ref:`Checking Whether the Affected Path Is an OBS Path <modelarts_05_0032__en-us_topic_0000001177322949_en-us_topic_0166743701_section770714556555>`
#. :ref:`Checking Whether the Affected Path Is Available <modelarts_05_0032__en-us_topic_0000001177322949_en-us_topic_0166743701_section14650140565>`

.. _modelarts_05_0032__en-us_topic_0000001177322949_en-us_topic_0166743701_section770714556555:

Checking Whether the Affected Path Is an OBS Path
-------------------------------------------------

When using ModelArts, store your data in an OBS bucket. However, the OBS path cannot be used to read data during the execution of the training code.

The reason is as follows:

After a training job is created, the training performance is poor if the running container is directly connected to OBS. To prevent this issue, the system automatically downloads the training data to the local path of the running container. Therefore, an error occurs if an OBS path is used in training code.

If the affected path is a path to the training data, perform the following operations to resolve this issue (see input and output configurations for details):

#. When creating an algorithm, set the code path parameter, which defaults to **data_url**, in the input path mapping configuration.
#. Add a hyperparameter, which defaults to **data_url**, to the training code. Use **data_url** as the local path for inputting the training data.

.. _modelarts_05_0032__en-us_topic_0000001177322949_en-us_topic_0166743701_section14650140565:

Checking Whether the Affected Path Is Available
-----------------------------------------------

The code developed locally must be uploaded to the ModelArts backend. In training code, it is error-prone to set the path for storing the dependency file.

The following general solution is recommended: Use the OS API to obtain the absolute path of the dependency file.

Example:

.. code-block::

   |---project_root                # Root directory for code
      |---BootfileDirectory        # Directory where the boot file is located
        |---bootfile.py            # Boot file
      |---otherfileDirectory       # Directory of other dependency files
        |---otherfile.py           # Other dependency files


Do as follows to obtain the path of the dependency file, **otherfile_path** in this example, in the boot file:

.. code-block::

   import os
   current_path = os.path.dirname(os.path.realpath(__file__)) # Directory where the boot file is located
   project_root = os.path.dirname(current_path) # Root directory of the project, which is the code directory set on the ModelArts training console
   otherfile_path = os.path.join(project_root, "otherfileDirectory", "otherfile.py")
