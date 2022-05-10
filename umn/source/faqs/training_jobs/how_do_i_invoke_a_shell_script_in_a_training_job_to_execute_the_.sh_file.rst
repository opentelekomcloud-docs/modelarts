:original_name: modelarts_21_0085.html

.. _modelarts_21_0085:

How Do I Invoke a Shell Script in a Training Job to Execute the .sh File?
=========================================================================

ModelArts enables you to invoke a shell script, and you can use Python to invoke **.sh**. The procedure is as follows:

#. Upload the **.sh** script to an OBS bucket. For example, upload the **.sh** script to **/bucket-name/code/test.sh**.

#. Create the **.py** file on a local PC, for example, **test.py**. The background automatically downloads the code directory to the **/home/work/user-job-dir/** directory of the container. Therefore, you can invoke the **.sh** file in the **test.py** boot file as follows:

   .. code-block::

      import os
      os.system('bash /home/work/user-job-dir/code/test.sh')

#. Upload **test.py** to OBS. Then the file storage path is **/bucket-name/code/test.py**.

#. When creating a training job, set the code directory to **/bucket-name/code/**, and the boot file directory to **/bucket-name/code/test.py**.

After the training job is created, you can use Python to invoke the **.sh** file.
