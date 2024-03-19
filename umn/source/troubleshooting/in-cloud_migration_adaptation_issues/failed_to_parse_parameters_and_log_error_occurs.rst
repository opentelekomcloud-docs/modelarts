:original_name: modelarts_13_0012.html

.. _modelarts_13_0012:

Failed to Parse Parameters and Log Error Occurs
===============================================

Symptom
-------

The ModelArts training job failed to parse parameters, and the following error occurs:

.. code-block::

   error: unrecognized arguments: --data_url=xxx://xxx/xxx
   error: unrecognized arguments: --init_method=tcp://job

.. code-block::

   absl.flags._exceptions.UnrecognizedFlagError:Unknown command line flag 'task_index'

Possible Causes
---------------

#. The parameters are not defined.
#. In the training environment, the system may pass parameters that are not defined in the Python script. As a result, the parameters cannot be parsed, and an error is printed in the log.

Solution
--------

#. Define the parameters. The code example is as follows:

   .. code-block::

      parser.add_argument('--init_method', default='tcp://xxx',help="init-method")

#. Replace **args = parser.parse_args()** with **args, unparsed = parser.parse_known_args()**. The following is a code example.

   .. code-block::

      import argparse
      parser = argparse.ArgumentParser()
      parser.add_argument('--data_url', type=str, default=None, help='obs path of dataset')
      args, unparsed = parser.parse_known_args()
