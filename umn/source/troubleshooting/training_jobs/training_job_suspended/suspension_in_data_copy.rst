:original_name: modelarts_trouble_0110.html

.. _modelarts_trouble_0110:

Suspension in Data Copy
=======================

Symptom
-------

The system stops responding when **mox.file.copy_parallel** is called to copy data.

Solution
--------

-  Run the following commands to copy files or folders:

   .. code-block:: text

      import moxing as mox
      mox.file.set_auth(is_secure=False)

-  Run the following command to copy a single file that is greater than 5 GB:

   .. code-block:: text

      from moxing.framework.file import file_io

   Run **file_io._LARGE_FILE_METHOD** to check the version of the MoXing API. Output value **1** indicates V1 and **2** indicates V2.

   Run **file_io._NUMBER_OF_PROCESSES=1** to resolve the issue for the V1 API.

   To resolve the issue for the V2 API, run **file_io._LARGE_FILE_METHOD = 1** to switch to V1 and perform operations required in V1. Alternatively, run **file_io._LARGE_FILE_TASK_NUM=1** to resolve this issue.

-  Run the following command to copy a folder:

   .. code-block:: text

      mox.file.copy_parallel(threads=0,is_processing=False)
