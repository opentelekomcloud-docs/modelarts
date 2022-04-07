.. _modelarts_05_0031:

What Can I Do If the Message "Object directory size/quantity exceeds the limit" Is Displayed When I Create a Training Job?
==========================================================================================================================

Issue Analysis
--------------

The code directory for creating a training job has limits on the size and number of files.

Solution
--------

Delete the files except the code from the code directory or save the files in other directories. Ensure that the size of the code directory does not exceed 128 MB and the number of files does not exceed 4,096.
