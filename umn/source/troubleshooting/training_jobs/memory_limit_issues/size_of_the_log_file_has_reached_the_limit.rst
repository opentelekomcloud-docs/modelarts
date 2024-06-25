:original_name: modelarts_13_0032.html

.. _modelarts_13_0032:

Size of the Log File Has Reached the Limit
==========================================

Symptom
-------

An error occurs during the running of a ModelArts training job, indicating that the size of the log file has reached the limit.

.. code-block::

   modelarts-pope: log length overflow(max:1073741824; already: 107341771; new:90), process will continue running silently

Possible Cause
--------------

Error information indicates that the size of the log file has reached the limit. After this error occurs, the volume of logs does not increase and the background continues to run.

Solution
--------

Reduce unnecessary log output from the boot file.
