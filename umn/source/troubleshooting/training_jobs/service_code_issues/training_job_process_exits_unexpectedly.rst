:original_name: modelarts_13_0074.html

.. _modelarts_13_0074:

Training Job Process Exits Unexpectedly
=======================================

Symptom
-------

Running a training job failed, and error information similar to the following is displayed in logs:

.. code-block::

   [Modelarts Service Log]Training end with return code: 137

Possible Causes
---------------

According to the log, the exit code of the training job is 137. The training process starts after the user code is executed. Therefore, the exit code mentioned in this section is generated after the code for training job is executed. Common error codes include codes 247 and 139.

-  Exit code: 137 or 247

   The possible cause is that the memory overflows. To resolve this issue, you can reduce the data volume, decrease the **batch_size** value, optimize the code, or aggregate and replicate the data.

   .. note::

      The size of data files is not equal to the memory usage. Therefore, evaluate the memory usage.

-  Exit code: 139

   Check the version of the installation package. There may be a package conflict.

Troubleshooting
---------------

According to the error information, the error is caused by the user code.

You can use either of the following methods to locate the fault:

-  Debug the code online (only available for the non-distributed code).

   #. Apply for a development environment instance with the same specifications in the development environment (notebook).
   #. Debug the user code in the notebook and find the improper code snippet.
   #. Find a solution by searching the key code snippet and exit code in a search engine.

-  Locate the fault based on the training logs.

   #. Identify the improper code snippet based on the logs.
   #. Print the improper code snippet to obtain more detailed log information.
   #. Run the training job again to locate the improper code snippet.
