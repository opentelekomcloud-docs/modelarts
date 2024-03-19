:original_name: modelarts_13_0075.html

.. _modelarts_13_0075:

Stopped Training Job Process
============================

Symptom
-------

The training job process is stopped and the logs are interrupted.

Possible Causes
---------------

-  CPU soft lock

   The decompression of a large number of files may cause CPU soft lock and node restart. You can suspend the decompression for the specified amount of time by invoking sleep method when decompressing a large number of files. For example, every time 10,000 files are decompressed, the decompression stops for 1 second.

-  Storage limitation

   Use data disks based on specifications. For details about a data disk size, see

-  CPU overload

   Reduce the number of threads.

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
