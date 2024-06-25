:original_name: modelarts_trouble_0141.html

.. _modelarts_trouble_0141:

System Container Exits Unexpectedly
===================================

Symptom
-------

After a training job is created, the system container exits unexpectedly.

Possible Causes
---------------

The possible causes are as follows:

#. An error occurred in OBS.

   a. Unavailable file: The specified key does not exist.
   b. Insufficient OBS permissions
   c. OBS traffic limiting
   d. Others

#. The disk space is insufficient.

Solution
--------

#. For an OBS error:

   a. Unavailable file: The specified key does not exist.

      For details, see :ref:`Error Message "errorMessage:The specified key does not exist" Displayed in Logs <modelarts_trouble_0035>`.

   b. Insufficient OBS permissions

      For details, see :ref:`What Should I Do If Error "stat:403 reason:Forbidden" Is Displayed in Logs When a Training Job Accesses OBS <modelarts_trouble_0045>`.

   c. OBS traffic limiting

      For details, see :ref:`Error Message "BrokenPipeError: Broken pipe" Displayed When OBS Data Is Copied <modelarts_trouble_0042>`.

   d. Others

      Alternatively, collect the request ID and contact OBS customer service.

#. For insufficient disk space:

   For details, see :ref:`Common Issues Related to Insufficient Disk Space and Solutions <modelarts_trouble_0142>`.
