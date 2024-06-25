:original_name: modelarts_13_0012.html

.. _modelarts_13_0012:

Failed to Parse Parameters and Log Error Occurs
===============================================

Symptom
-------

The ModelArts training job failed to parse parameters, and the following error occurs:

.. code-block::

   error: unrecognized arguments: --data_url=xxx://xxx/xxx

.. code-block::

   absl.flags._exceptions.UnrecognizedFlagError:Unknown command line flag 'task_index'

Possible Cause
--------------

In the training environment, the system may transfer other parameter names that are not defined in the Python script. As a result, the parameters failed to be parsed, and an error occurs in the log.

Solution
--------

Replace **args = parser.parse_args()** with the **args, unparsed = parser.parse_known_args()** parsing method. The following is a code example.

.. code-block::

   import argparse
   parser = argparse.ArgumentParser()
   parser.add_argument('--data_url', type=str, default=None, help='obs path of dataset')
   args, unparsed = parser.parse_known_args()
