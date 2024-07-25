:original_name: modelarts_13_0034.html

.. _modelarts_13_0034:

Training Job Failed Because the Maximum Recursion Depth Is Exceeded
===================================================================

Symptom
-------

An error occurs for a ModelArts training job.

.. code-block::

   RuntimeError: maximum recursion depth exceeded in __instancecheck__

Possible Causes
---------------

The training failed because the recursion depth exceeded the default recursion depth of Python.

Solution
--------

If the maximum recursion depth is exceeded, increase the recursion depth in the boot file as follows:

.. code-block::

   import sys
   sys.setrecursionlimit(1000000)
