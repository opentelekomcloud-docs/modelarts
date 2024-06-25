:original_name: modelarts_13_0043.html

.. _modelarts_13_0043:

Insufficient Container Space for Copying Data
=============================================

Symptom
-------

When a ModelArts training job is running, the following error is reported in the log. As a result, data cannot be copied to the container.

.. code-block::

   OSError:[Errno 28] No space left on device

Possible Causes
---------------

The container space is insufficient for downloading data.

Solution
--------

#. Check whether data is downloaded to the **/cache** directory. Each GPU node has a **/cache** directory with 4 TB of storage.

#. Check whether GPU resources are used. If CPU resources are used, **/cache** and the code directory share 10 GB of memory. As a result, the memory is insufficient. In this case, use GPU resources instead.

#. Add the following environment variable to the code:

   .. code-block::

      import os
      os.system('export TMPDIR=/cache')
